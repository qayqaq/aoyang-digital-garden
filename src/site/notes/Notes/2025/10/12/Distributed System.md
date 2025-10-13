---
{"dg-publish":true,"permalink":"/notes/2025/10/12/distributed-system/"}
---

#computer-science/distributed-systems
[[Distributed System.canvas\|Distributed System.canvas]]

# Distributed Systems

## 1. Introduction

A **distributed system** is a collection of autonomous computing elements, often referred to as **nodes** or **processes**, that are interconnected by a network and communicate by passing messages. To its users, a well-designed distributed system appears as a single, coherent computational entity. This abstraction conceals the underlying complexity of coordination, communication, and failure handling across multiple machines.

The significance of distributed systems is paramount in modern computing. They form the architectural foundation for the internet, [[Notes/2025/10/12/Cloud Computing\|Cloud Computing]], large-scale data processing frameworks (like [[Notes/2025/10/12/Apache Spark\|Apache Spark]]), [[Notes/2025/10/12/Blockchain\|Blockchain]] technologies, and modern [[Notes/2025/10/12/Microservice\|Microservice]]-based applications. Understanding their principles is essential for building systems that are **scalable**, **resilient**, and **highly available**.

> "A distributed system is one in which the failure of a computer you didn't even know existed can render your own computer unusable." — Leslie Lamport

This quote aptly captures the core challenge and defining characteristic of these systems: **partial failure**.

## 2. Core Goals and Characteristics

Distributed systems are designed to achieve several key objectives that are difficult or impossible to attain with a single, monolithic system.

### 2.1. Scalability
Scalability is the system's ability to handle a growing amount of work by adding resources. There are two primary dimensions to scaling:
-   **Horizontal Scaling (Scaling Out)**: Adding more nodes to the system. This is the predominant scaling strategy for distributed systems, as it allows for potentially limitless growth.
-   **Vertical Scaling (Scaling Up)**: Increasing the resources (CPU, RAM, storage) of a single node. This approach has inherent physical and cost limitations.

### 2.2. High Availability and Fault Tolerance
A key driver for distributed architecture is the pursuit of continuous operation.
-   **High Availability**: The system is designed to remain operational and accessible for a high percentage of time, often measured in "nines" (e.g., 99.999% uptime).
-   **Fault Tolerance**: The system can continue to function correctly even in the event of failures in one or more of its components (e.g., node crashes, network disruptions). This is typically achieved through **redundancy**—replicating data and computation across multiple nodes.

### 2.3. Transparency
Transparency refers to the concealment of the system's distributed nature from users and application developers. The goal is to present the system as a single, integrated whole. Key forms of transparency include:
-   **Location Transparency**: Users do not need to know the physical location of resources.
-   **Access Transparency**: The methods for accessing local and remote resources are identical.
-   **Replication Transparency**: The existence of multiple copies of a resource is hidden from the user.
-   **Failure Transparency**: The system automatically conceals the failure and recovery of components.

## 3. Fundamental Challenges

The benefits of distributed systems come at the cost of significant complexity. Engineers must contend with challenges that do not exist in single-machine environments.

### 3.1. Partial Failure
Unlike a centralized system that typically fails all at once, a distributed system can experience **partial failures**. One node may crash while others continue to operate, or a network link may fail, isolating a subset of nodes. Detecting and recovering from such failures is a non-trivial problem.

### 3.2. Concurrency and Coordination
Multiple processes execute simultaneously and may attempt to access shared resources. This necessitates sophisticated mechanisms for coordination and synchronization to prevent data corruption and ensure consistent state across the system.

### 3.3. Network Unreliability and Latency
Communication in a distributed system occurs over a network, which is inherently unreliable.
-   **Messages can be lost, delayed, duplicated, or delivered out of order.**
-   **Network Latency** (the time it takes for a message to travel from one node to another) is non-zero and variable. This delay has profound implications for system performance and consistency.

### 3.4. Consensus
**Consensus** is the task of getting a group of processes to agree on a single value or decision. It is a fundamental problem in distributed computing and is essential for tasks like electing a leader or committing a transaction in a distributed database. Algorithms like **Paxos** and **Raft** are designed to solve this problem in the face of failures.

## 4. The CAP Theorem

The **CAP Theorem**, also known as Brewer's Theorem, is a foundational principle in distributed system design. It states that it is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees:

1.  **Consistency (C)**: Every read operation receives the most recent write or an error. In a consistent system, all nodes see the same data at the same time.
2.  **Availability (A)**: Every request receives a (non-error) response, without the guarantee that it contains the most recent write. The system remains operational for both reads and writes.
3.  **Partition Tolerance (P)**: The system continues to operate despite an arbitrary number of messages being dropped or delayed by the network between nodes (i.e., a "network partition").

Since network partitions are an unavoidable reality in any large-scale distributed system, the theorem forces a trade-off between consistency and availability.
-   **CP (Consistency and Partition Tolerance)**: In the event of a partition, the system will sacrifice availability to maintain consistency. It may return an error or time out until the partition is resolved. Many distributed databases, like Google's Spanner, are in this category.
-   **AP (Availability and Partition Tolerance)**: In the event of a partition, the system will sacrifice consistency to remain available. It will respond to requests, but the data returned may be stale. This model is often described as **eventual consistency**. Systems like Amazon's DynamoDB and Apache Cassandra are designed this way.

## 5. Architectural Models

Distributed systems can be organized in various ways, each with its own trade-offs.
-   **Client-Server**: A traditional model where powerful servers provide services to multiple, less powerful clients.
-   **Peer-to-Peer (P2P)**: All nodes are peers with equal roles and responsibilities, acting as both clients and servers. Examples include BitTorrent and some blockchain networks.
-   **Microservices**: An architectural style that structures an application as a collection of small, autonomous, and loosely coupled services. Each service is independently deployable and scalable, communicating with others typically over a network via APIs. This is the dominant architecture for modern, complex web applications.

## 6. Conclusion

Distributed systems are the engine of the modern digital world, enabling global-scale services that are both resilient and performant. However, their design requires a deep understanding of the inherent trade-offs between consistency, availability, and fault tolerance, as well as the fundamental challenges posed by concurrency, partial failure, and network unreliability. As technology moves towards edge computing, the Internet of Things (IoT), and even more interconnected systems, the principles of distributed computing will only become more critical.
