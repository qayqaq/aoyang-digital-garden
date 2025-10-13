---
{"dg-publish":true,"permalink":"/notes/2025/10/12/system-design/"}
---

#system-design #software-architecture #scalability #distributed-systems
[[System Design.canvas\|System Design.canvas]]

# System Design: Principles and Practices

## 1. Introduction to System Design

**System Design** is the process of defining the architecture, components, modules, interfaces, and data for a system to satisfy a specified set of functional and non-functional requirements. It serves as the conceptual blueprint that bridges the gap between user requirements and the concrete implementation of a software system. The primary objective is to engineer systems that are not only functional but also **scalable**, **reliable**, **available**, and **maintainable**.

At its core, system design is an exercise in managing complexity and making informed trade-offs. There is rarely a single "correct" solution; instead, engineers must balance competing constraints—such as cost, performance, and consistency—to arrive at an optimal architecture for a given problem domain.

## 2. Foundational Principles

Every robust system is built upon a set of core principles that dictate its behavior under various conditions.

### 2.1. Scalability

Scalability is the property of a system to handle a growing amount of work by adding resources. There are two primary dimensions to scaling:

-   **Vertical Scaling (Scaling Up)**: This involves increasing the capacity of a single machine, for instance, by adding more CPU, RAM, or storage. While simple to implement, it has a finite limit and can become prohibitively expensive.
-   **Horizontal Scaling (Scaling Out)**: This involves distributing the workload across multiple machines (nodes). This approach is the cornerstone of modern distributed systems, offering potentially limitless scalability and higher fault tolerance.

### 2.2. Availability

Availability refers to the proportion of time a system is operational and capable of fulfilling its intended function. It is commonly expressed as a percentage of uptime, often measured in "nines."

| Availability % | Downtime per Year |
| :-- | :-- |
| 99% ("two nines") | 3.65 days |
| 99.9% ("three nines") | 8.77 hours |
| 99.99% ("four nines") | 52.6 minutes |
| 99.999% ("five nines") | 5.26 minutes |

The formula for availability is:
$$
\text{Availability} = \frac{\text{Uptime}}{\text{Uptime} + \text{Downtime}} \times 100\%
$$
High availability is typically achieved through **redundancy** (duplicating critical components) and **failover** mechanisms that automatically switch to a standby system upon failure.

### 2.3. Performance and Latency

-   **Latency**: The time delay experienced by a user or system when waiting for a response to an action. It is the time from the initiation of a request to the receipt of the response.
-   **Throughput**: The rate at which a system can process requests, often measured in requests per second (RPS) or transactions per second (TPS).

Optimizing for low latency and high throughput is a primary goal of system design, often involving techniques like caching, load balancing, and efficient data retrieval.

### 2.4. Consistency

In the context of distributed systems, consistency ensures that all nodes in a cluster see the same data at the same time. Different levels of consistency exist:

-   **Strong Consistency**: Guarantees that any read operation will return the value of the most recent write. This is the easiest model to reason about but can introduce higher latency.
-   **Eventual Consistency**: Guarantees that, if no new updates are made to a given data item, all accesses to that item will eventually return the last updated value. This model prioritizes availability and low latency over immediate consistency.

## 3. Core Architectural Components

Modern distributed systems are constructed from a set of well-understood building blocks.

### 3.1. Load Balancer

A load balancer is a device or service that distributes network or application traffic across multiple servers. This serves two main purposes:
1.  **Preventing Overload**: Ensures that no single server becomes a bottleneck.
2.  **Improving Availability**: If one server fails, the load balancer can redirect traffic to the remaining healthy servers.

Common load balancing algorithms include **Round Robin**, **Least Connections**, and **IP Hashing**.

### 3.2. Caching

A cache is a high-speed data storage layer that stores a subset of data, typically transient, so that future requests for that data are served up faster than is possible by accessing the data's primary storage location.

> Caching is a powerful technique to reduce latency and decrease the load on backend systems like databases. Common strategies include the [[Notes/2025/10/12/Cache-Aside Pattern\|Cache-Aside Pattern]], Write-Through, and Write-Back caching.

### 3.3. Databases

The choice of data store is a critical architectural decision.
-   **SQL (Relational) Databases**: Offer structured data storage with ACID (Atomicity, Consistency, Isolation, Durability) guarantees. They are well-suited for applications requiring strong consistency and complex transactions. Examples: PostgreSQL, MySQL.
-   **NoSQL (Non-Relational) Databases**: Provide more flexible data models (key-value, document, column-family, graph) and are often designed for horizontal scalability and high availability. Examples: Cassandra, [[Notes/2025/10/11/MongoDB\|MongoDB]], [[Notes/2025/10/12/Redis\|Redis]].

Database scaling techniques include **replication** (creating copies of data), **sharding** (partitioning data across multiple databases), and **partitioning**.

### 3.4. Message Queues

Message queues enable **asynchronous communication** between different parts of a system. A service (the *producer*) publishes a message to a queue, and another service (the *consumer*) processes the message at a later time. This pattern **decouples** services, allowing them to evolve independently and improving the system's resilience to failures.

### 3.5. Content Delivery Network (CDN)

A CDN is a geographically distributed network of proxy servers that cache static content (e.g., images, CSS, JavaScript files) closer to end-users. By serving content from a nearby edge server, a CDN significantly reduces latency and offloads traffic from the origin servers.

## 4. Fundamental Theorems

Theoretical frameworks provide essential guidance for designing distributed systems.

### 4.1. The CAP Theorem

The CAP theorem, also known as Brewer's theorem, states that it is impossible for a distributed data store to simultaneously provide more than two of the following three guarantees:

1.  **Consistency (C)**: Every read receives the most recent write or an error.
2.  **Availability (A)**: Every request receives a (non-error) response, without the guarantee that it contains the most recent write.
3.  **Partition Tolerance (P)**: The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes.

In a distributed system, network partitions are a reality, so **Partition Tolerance (P) is a necessity**. Therefore, the trade-off is always between Consistency and Availability.
-   **CP Systems**: Choose consistency over availability. During a partition, they may become unavailable to guarantee that remaining nodes are consistent.
-   **AP Systems**: Choose availability over consistency. During a partition, they remain available but may return stale data.

### 4.2. The PACELC Theorem

The PACELC theorem extends CAP by addressing the trade-offs that occur in the absence of a network partition. It states:
> If there is a **P**artition, a distributed system must trade between **A**vailability and **C**onsistency. **E**lse (when the system is running normally), it must trade between **L**atency and **C**onsistency.

This provides a more complete framework for analyzing system behavior during both normal and failure conditions.

## 5. A Systematic Approach to Design

A structured approach is crucial for tackling complex system design problems.

1.  **Clarify Requirements**: Distinguish between **functional requirements** (what the system must do) and **non-functional requirements** (how the system must perform, e.g., latency, availability, scalability targets).
2.  **Back-of-the-Envelope Estimation**: Perform rough calculations to estimate the scale of the system (e.g., users, requests per second, storage needs, bandwidth). This helps in making informed technology choices.
3.  **High-Level Design**: Sketch the main components and their interactions. Create a block diagram showing clients, load balancers, web servers, application servers, and databases.
4.  **Deep Dive**: Refine the design of individual components. Discuss API design, database schema, caching strategies, and data partitioning schemes.
5.  **Identify Bottlenecks and Trade-offs**: Analyze the design for single points of failure, potential performance bottlenecks, and scalability limitations. Explicitly state the trade-offs made (e.g., choosing eventual consistency for higher availability).

## 6. Conclusion

System design is a multifaceted discipline that combines principles of computer science, software engineering, and operational management. It is fundamentally about building systems that can withstand the pressures of scale, failure, and evolving requirements. As technology progresses with trends like microservices, serverless computing, and AI-driven applications, the principles of balancing trade-offs, ensuring resilience, and planning for scale will remain the enduring cornerstones of effective system design.

