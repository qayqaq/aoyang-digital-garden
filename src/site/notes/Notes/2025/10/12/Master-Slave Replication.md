---
{"dg-publish":true,"permalink":"/notes/2025/10/12/master-slave-replication/"}
---

#database #replication #high-availability #scalability #cloud-native

[[Master-Slave Replication.canvas\|Master-Slave Replication.canvas]]

# Master-Slave (Primary-Replica) Replication

## 1. Introduction

**Master-Slave Replication**, more commonly referred to in modern terminology as **Primary-Replica** or **Primary-Secondary Replication**, is a foundational architectural pattern for creating copies of a database across multiple servers. In this model, one server acts as the **master** (or primary), serving as the single authoritative source for all data modifications. One or more other servers, known as **slaves** (or replicas), maintain an exact copy of the master's data by asynchronously or synchronously applying the changes made on the master.

The significance of this architecture lies in its ability to address several critical system requirements simultaneously: enhancing **read scalability**, ensuring **high availability**, and providing robust **data redundancy**. It is one of the most widely implemented strategies for scaling and protecting database systems, from traditional relational databases like MySQL and PostgreSQL, to NoSQL systems like [[Notes/2025/10/12/Redis\|Redis]], and forming the conceptual basis for modern cloud-native databases like [[Notes/2025/10/12/PolarDB\|PolarDB]].

> **A Note on Terminology**: The terms "master" and "slave" are being phased out in the technology industry in favor of more inclusive and descriptive language like "primary" and "replica" or "secondary." This note will use both sets of terms, with a preference for the modern nomenclature, to ensure comprehensive understanding.

## 2. Core Architecture and Process

The primary-replica model is defined by a unidirectional flow of data from a single primary node to one or more replica nodes.

### 2.1. Key Components
- **Primary (Master)**: The single node in the replication cluster that accepts all **write operations** (e.g., `INSERT`, `UPDATE`, `DELETE`). It is the definitive source of truth for the dataset.
- **Replica (Slave)**: A node that maintains a copy of the primary's data. It cannot accept direct writes from clients and is typically used to serve **read operations**.
- **Replication Log (e.g., Binary Log)**: A transaction log on the primary server that records every data-modifying event in the order it was committed. This log is the fundamental mechanism that enables replication.

### 2.2. The Replication Workflow
The process of propagating changes from the primary to a replica generally follows these steps:

1.  **Client Write**: A client application sends a write query to the primary database.
2.  **Transaction Commit and Logging**: The primary executes the transaction. Upon successful commit, it writes a record of the change to its **replication log** (e.g., the `binlog` in MySQL).
3.  **Log Transmission**: A dedicated I/O thread on the replica connects to the primary and requests any new entries from the replication log. The primary's dump thread sends these new log entries over the network to the replica.
4.  **Relay Log Storage**: The replica's I/O thread receives the log entries and writes them to a local file known as the **relay log**. This step decouples the process of receiving updates from applying them, making the system more resilient to network fluctuations.
5.  **Log Application**: A separate SQL thread on the replica reads the events from its relay log and executes them in the exact same order they were executed on the primary. This action updates the replica's dataset, bringing it into sync with the primary.

## 3. Replication Modes: Consistency vs. Performance

The guarantee of when a transaction is considered complete depends on the replication mode, which presents a critical trade-off between performance and data consistency.

### 3.1. Asynchronous Replication
This is the most common mode. The primary commits a transaction and responds to the client immediately after writing to its local replication log. The log entries are sent to replicas afterward, without the primary waiting for any acknowledgment.

- **Pros**: Offers the highest write performance and lowest latency, as the primary is not blocked by network or replica speed.
- **Cons**: Carries a risk of data loss. If the primary fails before the un-replicated log entries are sent to any replica, those transactions are lost. This leads to **replication lag**.

### 3.2. Synchronous Replication
In this mode, the primary waits to confirm a transaction commit to the client until at least one (or all, depending on configuration) replica has acknowledged that it has received *and applied* the change.

- **Pros**: Guarantees zero data loss on failover (high consistency), as a committed transaction is certain to exist on at least one replica.
- **Cons**: Significantly increases write latency on the primary, as it must wait for network round-trip time and replica processing. The system's overall write throughput is limited by the slowest replica.

### 3.3. Semi-Synchronous Replication
This mode offers a compromise. The primary commits a transaction and waits for acknowledgment from at least one replica that it has *received* the log entry (typically written to its relay log), but not necessarily that it has been applied.

- **Pros**: Provides a stronger durability guarantee than asynchronous replication while avoiding the high latency penalty of fully synchronous replication.
- **Cons**: Still introduces more latency than the asynchronous mode.

## 4. Key Use Cases and Benefits

1.  **Read Scalability**: By directing all write traffic to the primary and distributing read traffic across multiple replicas, the system can handle a much higher volume of total requests. The total read throughput ($R_{total}$) scales with the number of replicas ($N$):
    $$
    R_{total} = \sum_{i=1}^{N} R_{replica_i}
    $$
2.  **High Availability (HA)**: If the primary node fails, a replica can be promoted to become the new primary. This **failover** process, often automated by tools like **Redis Sentinel** or Patroni for PostgreSQL, minimizes system downtime.
3.  **Data Redundancy and Backups**: Replicas serve as real-time, hot copies of the data. A replica can be temporarily taken offline to perform a backup without impacting the availability of the primary node.
4.  **Analytics and Reporting**: Long-running, resource-intensive analytical queries can be executed on a dedicated replica. This isolates the analytical workload (OLAP) from the transactional workload (OLTP) on the primary, preventing performance degradation.

## 5. Challenges and Considerations

- **Replication Lag**: In asynchronous systems, there is an inherent delay between a write occurring on the primary and it being reflected on a replica. This lag, $\Delta t$, is the difference between the time of application on the replica ($T_{replica}$) and the time of commit on the primary ($T_{primary}$):
  $$
  \Delta t = T_{replica} - T_{primary}
  $$
  Applications reading from replicas must be designed to tolerate potentially stale data.

- **Single Point of Failure for Writes**: The primary node is a single point of failure for write operations. If it becomes unavailable, the system cannot accept any new data until a failover is completed.

- **Failover Complexity**: Automating the failover process is non-trivial. It requires reliable failure detection, a consensus mechanism for promoting the most up-to-date replica, and a strategy for reconfiguring other replicas and client connections to the new primary.

- **Split-Brain Scenarios**: A network partition could isolate the primary from the replicas and the failover mechanism. If the failover system incorrectly assumes the primary is down and promotes a replica, there will be two active primary nodes, leading to data divergence and corruption.

## 6. Architectural Evolution: The Shared-Storage Model (e.g., PolarDB)

The traditional primary-replica model is based on a "shared-nothing" architecture, where each node maintains its own complete copy of the data on local storage. While effective, this model introduces inherent challenges like replication lag. Cloud-native databases like **Alibaba Cloud's PolarDB** have pioneered an evolution of this pattern using a **shared-storage architecture**.

This modern approach decouples compute from storage. Instead of each replica storing a full data copy, all nodes (both primary and replicas) connect to a single, logical, distributed storage volume.

### 6.1. Core Concept and Workflow

In a shared-storage model, the replication process is fundamentally different:

1.  **Shared Log Stream**: When the primary node executes a write operation, it writes the **redo logs** to a shared, distributed log stream on the storage layer. It also writes the modified data pages to the shared storage.
2.  **Log-Based Replication**: Replica nodes do not receive logs from the primary over the network. Instead, they **read the same redo log stream** directly from the shared storage layer.
3.  **In-Memory Application**: Replicas apply these log records to their in-memory buffer cache to update their view of the data, enabling them to serve up-to-date read queries.

This means data is only written once to the durable storage layer by the primary. Replicas achieve synchronization by replaying the log, not by duplicating the entire dataset.

### 6.2. Key Advantages over Traditional Replication

This architecture directly addresses many of the classic challenges:

-   **Minimal Replication Lag**: Since replicas read from the same storage layer as the primary, the delay is reduced to the time it takes to read and apply the logs in memory. This typically brings replication lag down to the millisecond level, virtually eliminating the issue of stale reads.
-   **Instantaneous Failover**: If the primary node fails, a replica can be promoted almost instantly. Because the replica already has access to the complete, up-to-date data on the shared storage, there is no need to wait for data to be copied or for the replica to "catch up." The failover process is primarily about redirecting write traffic.
-   **Elastic Read Scalability**: Adding a new read replica is extremely fast. A new compute instance can be spun up, connect to the shared storage, and start serving read traffic immediately after warming its cache by replaying recent logs. This avoids the time-consuming process of copying the entire dataset to a new node.
-   **Reduced Storage Cost**: Data is not duplicated for each replica, leading to significant savings on storage costs, especially for large datasets with many read replicas.

## 7. Conclusion

Primary-Replica replication is a powerful and enduring architecture for building scalable, resilient, and highly available data systems. It provides a straightforward model for scaling read operations and ensuring business continuity. However, its benefits must be weighed against its inherent complexities, particularly the trade-offs between consistency and performance and the challenge of managing replication lag. While more complex multi-primary models and advanced cloud-native architectures like the shared-storage model have emerged to solve these challenges, the traditional Primary-Replica pattern remains a vital and widely implemented foundation in modern system design.

#### Sources:

- [[Notes/2025/10/12/Redis\|Redis]]
- [[Notes/2025/10/12/Master-Slave Replication\|Master-Slave Replication]]
- [[Notes/Arxiv/Place Cells as Proximity-Preserving Embeddings From Multi-Scale Random Walk to Straight-Forward Path Planning (2505.14806v3)\|Place Cells as Proximity-Preserving Embeddings From Multi-Scale Random Walk to Straight-Forward Path Planning (2505.14806v3)]]
- [[Notes/Arxiv/On the Trajectory Regularity of ODE-based Diffusion Sampling (2405.11326v1)\|On the Trajectory Regularity of ODE-based Diffusion Sampling (2405.11326v1)]]
- [[Notes/Arxiv/A Phase Transition in Diffusion Models Reveals the Hierarchical Nature of Data (2402.16991v3)\|A Phase Transition in Diffusion Models Reveals the Hierarchical Nature of Data (2402.16991v3)]]
- [[Excalidraw/Drawing 2025-10-12 14.15.50.excalidraw\|Drawing 2025-10-12 14.15.50.excalidraw]]
- [[Excalidraw/Drawing 2025-10-12 14.17.49.excalidraw\|Drawing 2025-10-12 14.17.49.excalidraw]]