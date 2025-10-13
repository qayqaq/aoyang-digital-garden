---
{"dg-publish":true,"permalink":"/notes/2025/10/12/cache-avalanche/"}
---

#cache #system-design #distributed-systems #fault-tolerance

[[Cache Avalanche.canvas\|Cache Avalanche.canvas]]

# Cache Avalanche

## 1. Introduction

A **Cache Avalanche** is a critical failure mode in distributed systems where a large number of cache entries expire or become invalidated simultaneously. This sudden mass expiration leads to a flood of requests bypassing the cache and directly hitting the backend data store (e.g., a database). This surge in traffic, analogous to an avalanche, can overwhelm the backend system, causing a sharp increase in latency, service degradation, or a complete system-wide outage.

The significance of this phenomenon lies in its potential to trigger a cascading failure. A system operating under normal load can be pushed into an unrecoverable state because the very component designed to protect the database—the cache—suddenly becomes ineffective. Understanding and mitigating the risk of a cache avalanche is therefore a fundamental aspect of designing resilient and scalable applications.

## 2. The Mechanism of a Cache Avalanche

To understand the failure, it is useful to contrast normal operation with the avalanche scenario.

### 2.1. Normal Operation (Steady State)

In a typical steady-state operation, the caching layer sits between the application and the database, absorbing a significant portion of the read traffic.

1.  An application requests data for a specific key.
2.  It first checks the cache. If the data is present (**cache hit**), it is returned immediately, and the database is not queried.
3.  If the data is not in the cache (**cache miss**), the application queries the database.
4.  The application then populates the cache with the retrieved data and sets an expiration time (Time-To-Live or TTL).
5.  The data is returned to the client.

Under this model, the database load is a fraction of the total request volume, determined by the cache hit rate, $H$.

$$
L_{db\_normal} = R_{total} \times (1 - H)
$$

Where $L_{db\_normal}$ is the database load and $R_{total}$ is the total request rate.

### 2.2. The Avalanche Trigger and Cascade

The avalanche is triggered when the system deviates from its steady state due to mass cache invalidation.

1.  **The Trigger**: A large volume of cache keys, often set with the same TTL, expire at the exact same moment. This commonly occurs after a system deployment, a cache cluster restart, or a bulk data import.
2.  **Mass Cache Misses**: Subsequent requests for this expired data result in simultaneous cache misses.
3.  **Database Overload**: All these requests are forwarded directly to the backend database. The database, which was sized to handle the normal miss rate, is now confronted with a traffic volume approaching the total application request rate ($L_{db\_avalanche} \approx R_{total}$).
4.  **System Failure**: The database CPU, memory, and I/O resources are exhausted. Its response time skyrockets, and it may begin to time out or crash.
5.  **Failure Loop**: Because the database is slow or unresponsive, the application cannot retrieve data to repopulate the cache. The cache remains empty, ensuring that all new requests continue to hammer the already-failing database, preventing recovery.

## 3. Primary Causes

A cache avalanche is typically initiated by one of the following events:

-   **Simultaneous Key Expiration**: This is the most common cause. For example, if a service starts at midnight and caches data for 24 hours, all that data will expire simultaneously at midnight the next day.
-   **Cache Server Failure**: The failure of a significant portion of the cache cluster (e.g., a Redis master node going down without a proper failover). This instantly invalidates all keys stored on the failed nodes.
-   **Network Partition**: A network failure that isolates the application servers from the cache cluster, rendering the cache inaccessible and forcing all traffic to the database.

## 4. Prevention and Mitigation Strategies

A multi-layered defense is the most effective approach to preventing cache avalanches. The core principle is to avoid the simultaneous execution of database queries.

### 4.1. Randomized Expiration Times (TTL Jitter)

This is the simplest and most effective preventative measure. Instead of assigning a fixed TTL to all keys of a certain type, a small, random value is added to the expiration time. This "jitter" spreads the expirations over a time window, smoothing out the load on the database.

For a base TTL, $T_{base}$, the effective TTL, $T_{effective}$, is calculated as:

$$
T_{effective} = T_{base} + \delta
$$

Where $\delta$ is a random variable drawn from a uniform distribution, for example, $\delta \sim U(0, T_{jitter})$.

**Example**: Instead of all keys expiring in 3600 seconds, they are set to expire between 3600 and 3900 seconds.

### 4.2. High Availability (HA) Cache Cluster

To mitigate avalanches caused by hardware or network failures, the cache cluster itself must be resilient. This involves:
-   **Replication**: Using patterns like [[Notes/2025/10/12/Master-Slave Replication\|Master-Slave Replication]] to create copies of cache data.
-   **Automatic Failover**: Employing systems like Redis Sentinel or managed cloud services (e.g., AWS ElastiCache) that can automatically promote a replica to a primary if the main node fails.
-   **Distribution**: Spreading cache data across multiple nodes (sharding) and availability zones to minimize the impact of a single point of failure.

### 4.3. Cache Regeneration Locking (Single-Flighting)

For extremely popular ("hot") keys, even with jitter, a cache miss can lead to multiple concurrent database queries for the same data. A locking mechanism ensures that only one thread or process is responsible for regenerating the cache value.

The process, often called **single-flighting**, works as follows:
1.  A request results in a cache miss for key `K`.
2.  The process attempts to acquire a distributed lock for `K`.
3.  If the lock is acquired, this process queries the database, repopulates the cache, and releases the lock.
4.  Other processes that miss on `K` while the lock is held will either wait for the lock to be released (and then read the newly cached value) or return a stale/default value, rather than hitting the database themselves.

```pseudocode
function get_data(key):
  value = cache.get(key)
  if value is null:
    // Attempt to acquire a lock for this key with a short timeout
    if lock.acquire("lock_for_" + key, timeout=100ms):
      try:
        // Double-check cache in case another thread populated it
        value = cache.get(key)
        if value is null:
          value = database.query(key)
          cache.set(key, value, ttl=calculate_randomized_ttl())
      finally:
        lock.release("lock_for_" + key)
    else:
      // Could not acquire lock, wait briefly and retry
      sleep(50ms)
      return cache.get(key) // Return value, which may now be populated
  return value
```

### 4.4. Rate Limiting and Circuit Breakers

These are secondary lines of defense that protect the database when other measures fail.
-   **Rate Limiter**: The application can limit the rate of outgoing requests to the database, preventing it from being completely overwhelmed.
-   **Circuit Breaker**: This pattern monitors the health of the database. If error rates or latency exceed a threshold, the circuit "trips," and the application temporarily stops sending requests, giving the database time to recover.

## 5. Distinction from Related Caching Problems

It is important to distinguish Cache Avalanche from two other common caching failure modes:

> -   **Cache Penetration**: Occurs when requests are made for data that **does not exist** in either the cache or the database. These malicious or accidental queries always bypass the cache and hit the database. It is typically solved using Bloom filters or by caching "not found" responses.
> -   **Cache Breakdown**: Refers to the expiration of a **single, extremely popular** key. The resulting flood of concurrent requests for that one key overloads the database. This is the specific problem that the single-flighting/locking mechanism is designed to solve.

A cache avalanche can be seen as a large-scale version of cache breakdown, involving many keys simultaneously.

## 6. Conclusion

A Cache Avalanche is a severe system-level threat that turns a performance-enhancing component into a catalyst for failure. Its root cause is the **simultaneity** of events—mass cache expirations that lead to a mass query load on the backend.

Effective prevention relies on a defense-in-depth strategy aimed at breaking this simultaneity. By introducing randomness into expiration times, building highly available cache clusters, and controlling the process of cache regeneration through locking, architects can design systems that are resilient to this catastrophic failure mode. Ultimately, preparing for cache avalanches is a crucial step in building robust, scalable, and reliable applications.

