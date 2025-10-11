---
{"dg-publish":true,"permalink":"/notes/2025/10/11/load-balancing/"}
---

#load-balancing #distributed-systems #networking #scalability

[[Load Balancing.canvas\|Load Balancing.canvas]]

# Load Balancing

## 1. Introduction

**Load balancing** is the methodical and efficient distribution of network or application traffic across multiple servers in a server farm or pool. The primary objective of load balancing is to optimize resource use, maximize throughput, minimize response time, and avoid overloading any single resource. By distributing the workload, a load balancer ensures that no single server bears too much demand, thereby improving the overall availability, reliability, and scalability of an application or service. In modern distributed systems, load balancing is not merely an option but a foundational component for building robust and high-performance architectures.

## 2. Core Principles and Objectives

The fundamental goal of load balancing is to prevent a single server from becoming a bottleneck. This is achieved by introducing a dispatcher, the **load balancer**, which acts as a "traffic cop" sitting in front of the servers and routing client requests across all servers capable of fulfilling those requests.

The main objectives are:
- **High Availability**: By distributing traffic among multiple servers and performing continuous **health checks**, a load balancer can automatically redirect traffic away from a failed or unhealthy server to the remaining operational servers. This process, known as **failover**, is critical for building fault-tolerant systems.
- **Scalability**: Load balancing facilitates horizontal scaling (scaling out), where system capacity is increased by adding more servers to the resource pool. The load balancer seamlessly incorporates new servers and begins sending them requests.
- **Performance**: By distributing the load, the system ensures that servers are not overwhelmed, which leads to lower latency and faster response times for users.
- **Maintainability**: Servers can be taken offline for maintenance, upgrades, or diagnostics without interrupting the overall service, as the load balancer will simply route traffic to the available servers.

## 3. Types of Load Balancers

Load balancers can be categorized based on the network layer at which they operate. This distinction determines the type of information they can use to make routing decisions.

### 3.1. Layer 4 (Transport Layer) Load Balancing

A **Layer 4 load balancer** operates at the transport layer of the OSI model. It makes its routing decisions based on information from the first few packets in the TCP/UDP stream, primarily the source and destination IP addresses and ports.

- **Mechanism**: It directs network packets to and from the upstream server without inspecting the content of the packets. This is a form of Network Address Translation (NAT).
- **Advantages**:
    - **High Performance**: Because it does not inspect packet content, it is extremely fast and has low computational overhead.
    - **Protocol Agnostic**: It can balance traffic for any protocol that uses TCP or UDP.
- **Disadvantages**:
    - **Limited Intelligence**: It has no awareness of the application-level content (e.g., HTTP headers, cookies, URL paths), so it cannot make routing decisions based on the specific nature of a request.

### 3.2. Layer 7 (Application Layer) Load Balancing

A **Layer 7 load balancer** operates at the application layer, the highest layer in the OSI model. It has access to the full content of the message and can make more sophisticated routing decisions.

- **Mechanism**: It terminates the network traffic, reads the message content, and makes a routing decision based on application-level information. It then establishes a new connection to the selected backend server.
- **Advantages**:
    - **Intelligent Routing**: It can route requests based on URLs, HTTP headers, cookies, and other application data. This allows for features like routing `/api/video` requests to a dedicated pool of video processing servers.
    - **SSL Offloading**: It can handle the decryption of incoming HTTPS requests, offloading the computationally expensive SSL/TLS handshake from the backend servers.
    - **Content Caching**: It can cache frequently accessed content to reduce requests to backend servers.
- **Disadvantages**:
    - **Higher Overhead**: Inspecting and processing application-level data requires more CPU and memory, making it slower than Layer 4 balancing.

## 4. Load Balancing Algorithms

The algorithm determines how the load balancer selects a backend server for each incoming request. The choice of algorithm depends on the specific needs of the application.

### 4.1. Static Algorithms

These algorithms distribute load without considering the current state or load of the servers.

- **Round Robin**: This is the simplest algorithm. It forwards requests to a list of servers in a circular order. While fair, it assumes all servers have identical capacity and are equally loaded.
- **Weighted Round Robin**: An extension of Round Robin where each server is assigned a **weight**, typically proportional to its processing capacity. A server with a higher weight receives a larger percentage of the traffic. If server $S_i$ has weight $w_i$, it will receive $w_i$ requests out of every $\sum_{j} w_j$ total requests.
- **IP Hash**: A hash of the client's source IP address is calculated to determine the destination server.
    $$
    \text{ServerIndex} = H(\text{IP}_{\text{client}}) \pmod{N}
    $$
    Where $H$ is a hash function and $N$ is the number of available servers. This method ensures that requests from a specific client are consistently directed to the same server, which is useful for maintaining **session persistence**.

### 4.2. Dynamic Algorithms

These algorithms take the current state of each server into account, such as its current load and response time.

- **Least Connections**: The load balancer directs new requests to the server with the fewest active connections. This is useful for applications where sessions may have a long duration. The next request is sent to server $j$ such that its active connection count $C_j$ is minimized:
    $$
    \text{SelectedServer} = \arg\min_{i} (C_i)
    $$
- **Weighted Least Connections**: This algorithm combines the concepts of server weight and active connections. The load is distributed based on the ratio of active connections to the server's weight. The goal is to send the next request to the server $j$ that minimizes this ratio:
    $$
    \text{SelectedServer} = \arg\min_{i} \left( \frac{C_i}{w_i} \right)
    $$
- **Least Response Time**: This algorithm forwards the request to the server with the fewest active connections and the lowest average response time. This requires the load balancer to actively monitor server health and performance via health checks.

## 5. Key Architectural Considerations

### 5.1. Health Checks

A critical function of a load balancer is to perform **health checks** on backend servers. It periodically sends a request (e.g., a TCP connect, an HTTP GET) to each server to verify that it is operating correctly. If a server fails a health check, the load balancer temporarily removes it from the pool of available servers and stops sending traffic to it until it becomes healthy again.

### 5.2. Session Persistence (Sticky Sessions)

For stateful applications, it is often necessary for all requests from a single user within a session to be handled by the same server. This is known as **session persistence** or **sticky sessions**. Layer 7 load balancers typically achieve this by inspecting cookies, while Layer 4 balancers can use the IP Hash method.

### 5.3. High Availability (HA) Configuration

Since the load balancer itself can become a single point of failure, it is common practice to deploy them in a high-availability pair. Common configurations include:
- **Active-Passive**: One load balancer actively handles traffic while a second, identical one remains on standby. If the active one fails, the passive one takes over.
- **Active-Active**: Both load balancers are active and share the traffic load. This configuration provides both redundancy and increased capacity.

## 6. Conclusion

Load balancing is an indispensable technology for modern application delivery. It is the cornerstone of building scalable, resilient, and high-performance systems. By intelligently distributing workloads, it ensures that applications can handle fluctuating traffic demands while maintaining a high quality of service for the end-user. As architectures evolve towards microservices, containers, and cloud-native environments, the role of load balancing has become even more critical, with sophisticated solutions like service meshes and cloud-integrated balancers providing dynamic and automated traffic management at an unprecedented scale.

