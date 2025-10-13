---
{"dg-publish":true,"permalink":"/notes/2025/10/12/polar-db/"}
---

#database #cloud-native #distributed-systems #storage #architecture

[[PolarDB.canvas\|PolarDB.canvas]]

# PolarDB: A Cloud-Native Relational Database Architecture

## 1. Introduction

**PolarDB** is a cloud-native relational database service developed by Alibaba Cloud, designed to deliver the performance and availability of high-end commercial databases while offering the simplicity and cost-effectiveness of open-source alternatives. Its fundamental innovation lies in the **decoupling of compute and storage**, a paradigm shift from traditional database architectures. This design allows for independent scaling of resources, near-instantaneous failover, and exceptional performance, making it a cornerstone of modern cloud infrastructure.

The significance of PolarDB stems from its ability to address the inherent limitations of classic "shared-nothing" database replication models, such as replication lag and slow scaling. By leveraging a shared-storage model, PolarDB provides a highly elastic, available, and performant database solution compatible with popular engines like MySQL, PostgreSQL, and Oracle.

## 2. Core Architecture: Decoupling Compute and Storage

The defining characteristic of PolarDB is its departure from the traditional shared-nothing architecture, where each database node manages its own dedicated compute, memory, and storage.

### 2.1. The Traditional "Shared-Nothing" Model

In a conventional primary-replica setup (e.g., standard MySQL replication), each server instance—both the primary and its replicas—maintains a complete, independent copy of the entire dataset on its local storage.

-   **Data Flow**: Writes are executed on the primary, recorded in a transaction log (e.g., `binlog`), and then transmitted over the network to the replicas, which apply these changes to their local data copies.
-   **Limitations**:
    *   **Replication Lag**: An inherent delay exists between the primary commit and the replica's update, leading to potentially stale reads.
    *   **Storage Inefficiency**: Data is duplicated across every node. For a dataset of size $S$ with $N$ replicas, the total storage required is $(N+1) \times S$.
    *   **Slow Scaling**: Adding a new replica requires copying the entire dataset, a process that can take hours or days for large databases.
    *   **Slow Failover**: Promoting a replica to primary may involve a lengthy process of ensuring it is fully synchronized, leading to significant downtime.

### 2.2. The PolarDB "Shared-Storage" Model

PolarDB re-architects this model by separating the database's computational tasks from its data storage tasks. All compute nodes in a cluster operate on a single, logical, shared copy of the data.

-   **Architecture**:
    *   **Compute Nodes**: A cluster consists of one **Primary Node** (handling read/write operations) and up to 15 **Read-Only Replicas** (handling read operations). These nodes are essentially stateless concerning persistent data; they primarily manage query processing, transaction logic, and in-memory data caching (e.g., the buffer pool).
    *   **Shared Storage Layer**: A single, highly available, and distributed storage volume holds all the data files, redo logs, and undo logs. This layer is designed for low latency and high I/O throughput.

> **Analogy**: Imagine a team of chefs (compute nodes) all working from a single, central pantry (shared storage). In the traditional model, each chef would need their own fully stocked pantry, and any new ingredient added to one would have to be manually delivered to all the others. In the PolarDB model, an ingredient is added once to the central pantry, and all chefs have immediate access to it.

## 3. Key Technical Mechanisms

The performance and efficiency of the shared-storage model are enabled by several key technological innovations.

### 3.1. Log-as-Database (Log is the Database)

This is the core mechanism for data propagation. Instead of replicating SQL statements or data pages, PolarDB leverages the redo log.

1.  **Primary Node Writes**: When a transaction is committed on the primary node, it writes the **redo log** records directly to the shared storage layer.
2.  **Replica Node Reads**: The read-only replicas do not receive data from the primary node via the network. Instead, they continuously read the same redo log stream from the shared storage.
3.  **In-Memory Application**: Replicas apply these log records to their in-memory buffer cache, thereby updating their view of the data.

This log-centric approach is a form of **physical replication** that is highly efficient and minimizes the delay between the primary and replicas, effectively reducing replication lag to milliseconds.

### 3.2. High-Speed Networking with RDMA

To minimize the latency between compute nodes and the storage layer, PolarDB utilizes **Remote Direct Memory Access (RDMA)**. This networking protocol allows a compute node to access the memory of a storage server directly, bypassing the CPU-intensive network stacks of both operating systems. This results in significantly lower latency and higher bandwidth compared to traditional TCP/IP communication, which is critical for I/O-intensive database operations.

## 4. Advantages of the PolarDB Architecture

The decoupling of compute and storage yields substantial benefits in scalability, availability, and cost.

### 4.1. Elastic Scalability

-   **Compute Scaling**: Adding or removing read replicas is exceptionally fast (typically completed within minutes). A new compute node simply needs to be provisioned and connected to the shared storage. It does not require a full data copy; it only needs to warm its cache by replaying recent logs.
-   **Storage Scaling**: The storage volume can be scaled up or down independently of the compute nodes, often automatically and without any service interruption.

### 4.2. High Availability and Rapid Failover

In the event of a primary node failure, a read replica can be promoted to become the new primary in under 30 seconds. This rapid failover is possible because the replica already has access to the complete and up-to-date data on the shared storage. The process involves a quick consensus check and redirection of client write traffic, not a time-consuming data synchronization.

### 4.3. High Performance

-   **Low-Latency Writes**: The primary node's write performance is not bottlenecked by waiting for replicas to acknowledge data receipt. It only needs to ensure the redo log is durably written to the shared storage.
-   **High Read Throughput**: Read workloads can be horizontally scaled across a large number of read replicas, all of which provide near-real-time data.

### 4.4. Cost-Effectiveness

The shared-storage model offers significant economic advantages:

-   **Reduced Storage Costs**: Data is stored only once. The storage cost for a dataset of size $S$ remains $S$, regardless of the number of replicas. This contrasts sharply with the $(N+1) \times S$ cost of the shared-nothing model.
-   **Efficient Backups**: Backups can be performed using storage-level snapshots, which are fast and have minimal impact on the performance of the database cluster.
-   **Pay-as-you-go**: Users can independently provision and pay for the exact amount of compute and storage resources they need.

## 5. Conclusion

PolarDB represents a significant evolution in relational database architecture, tailored specifically for the demands of the cloud era. By fundamentally rethinking the relationship between compute and storage, it overcomes the primary bottlenecks of traditional database systems. Its architecture delivers a powerful combination of enterprise-grade performance, massive scalability, and high availability, all while leveraging the economic efficiencies of the cloud. This shared-storage model has proven so effective that it has become a blueprint for other leading cloud-native databases, solidifying its position as a foundational technology for modern data-intensive applications.
