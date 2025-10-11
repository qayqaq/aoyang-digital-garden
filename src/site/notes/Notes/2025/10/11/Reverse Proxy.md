---
{"dg-publish":true,"permalink":"/notes/2025/10/11/reverse-proxy/"}
---

#networking #proxy #security
[[Reverse Proxy.canvas\|Reverse Proxy.canvas]]

# Reverse Proxy

## Introduction

A **reverse proxy** is a server that sits in front of one or more backend servers, acting as an intermediary for requests from clients to those servers. Unlike a forward proxy, which sits on the client-side and forwards requests to the internet, a reverse proxy operates on the server-side. It receives requests from the internet, forwards them to the appropriate backend server, and then returns the server's response to the client.

From the client's perspective, it appears to be communicating directly with a single, powerful origin server. The client has no awareness of the underlying backend infrastructure—its complexity, topology, or even its existence. This abstraction is the source of the reverse proxy's power and versatility, making it a cornerstone of modern web architecture for enhancing security, performance, and reliability.

## Core Functionality: The Request Flow

The fundamental operation of a reverse proxy involves intercepting and managing traffic between clients and servers. The process can be broken down into the following steps:

1.  **Client Request**: A client (e.g., a web browser) initiates a request for a resource by resolving a domain name (e.g., `www.example.com`) to an IP address.
2.  **DNS Resolution**: The domain's DNS records are configured to point to the IP address of the reverse proxy, not the backend servers.
3.  **Proxy Interception**: The reverse proxy receives the incoming HTTP request from the client.
4.  **Request Processing and Forwarding**: The proxy inspects the request (e.g., the requested URL path, headers) and, based on its configuration rules, determines which backend server should handle it. It then forwards the request to the selected internal server.
5.  **Backend Processing**: The backend server processes the request and generates a response.
6.  **Response to Proxy**: The backend server sends its response back to the reverse proxy.
7.  **Response to Client**: The reverse proxy receives the response and forwards it to the original client. The response appears to have originated directly from the reverse proxy itself.

This entire process is transparent to the client. The set of backend servers, denoted as $S = \{s_1, s_2, \dots, s_n\}$, is hidden behind the reverse proxy $P$. A client request $R_c$ is mapped by the proxy to a specific server $s_i \in S$ based on a routing function $f$.
$$
\text{Forward}(R_c) \rightarrow f(R_c) = s_i
$$
The response from $s_i$, denoted $R_s$, is then returned to the client via the proxy.

## Key Use Cases and Benefits

Reverse proxies are deployed to solve a multitude of architectural challenges. Their strategic position between clients and servers allows them to perform several critical functions simultaneously.

### 1. Load Balancing

Perhaps the most common use case, a reverse proxy can distribute incoming client requests across a pool of backend servers. This **load balancing** ensures that no single server becomes a bottleneck, thereby improving the overall availability, fault tolerance, and performance of the application. Common load balancing algorithms include:

-   **Round Robin**: Distributes requests sequentially to each server in the pool.
-   **Least Connections**: Forwards the request to the server with the fewest active connections.
-   **IP Hash**: Assigns a client to a specific server based on a hash of their IP address, ensuring session persistence.

### 2. Enhanced Security

A reverse proxy provides a significant security layer by abstracting the backend infrastructure.

-   **Hiding Backend Topology**: By concealing the IP addresses and characteristics of the backend servers, it makes it much more difficult for attackers to launch direct attacks against them.
-   **Web Application Firewall (WAF)**: It can be configured to inspect incoming traffic and filter out malicious requests, such as those associated with SQL injection, Cross-Site Scripting (XSS), and other common vulnerabilities.
-   **DDoS Mitigation**: As the single entry point, it can absorb and mitigate the impact of Distributed Denial of Service (DDoS) attacks before they reach the critical backend systems.

### 3. SSL/TLS Termination

A reverse proxy can handle the decryption and encryption of HTTPS traffic, a process known as **SSL/TLS termination**.

-   **Offloading CPU-Intensive Work**: The SSL/TLS handshake is computationally expensive. By offloading this task to the proxy, backend servers are freed to focus exclusively on processing application logic.
-   **Centralized Certificate Management**: SSL certificates only need to be installed and managed on the reverse proxy, simplifying deployment and renewal. Traffic between the proxy and the internal backend servers can then be unencrypted, operating within a trusted network.

### 4. Caching

The reverse proxy can store copies of frequently requested content in a **cache**. When a client requests a cached resource, the proxy can deliver it directly without needing to contact a backend server.

-   **Reduced Latency**: Serving content from the cache is significantly faster, improving the user experience.
-   **Decreased Backend Load**: By handling requests for static assets (images, CSS, JavaScript) and even some dynamic content, caching reduces the load on application servers.

### 5. Compression

To reduce the amount of data sent over the network, a reverse proxy can compress server responses (e.g., using Gzip or Brotli) before forwarding them to the client. The client's browser then decompresses the data. This reduces page load times, especially for users on slower connections.

### 6. Centralized Request Logging and Monitoring

Since all incoming requests pass through the reverse proxy, it serves as a natural chokepoint for logging and monitoring traffic. This provides a unified view of application usage and performance.

## Reverse Proxy vs. Forward Proxy

While both are types of proxies, their purpose and position within a network are fundamentally different.

| Feature | | Reverse Proxy | | Forward Proxy |
| :-- | :-- | :-- | :-- | :-- |
| **Position** | | Sits in front of **servers**. | | Sits in front of **clients**. |
| **Protects** | | The identity and infrastructure of the **server**. | | The identity of the **client**. |
| **Direction** | | Manages **incoming** requests from the internet to a server farm. | | Manages **outgoing** requests from clients to the internet. |
| **Primary Use Case** | | Load balancing, security, caching for a web service. | | Bypassing firewalls, filtering content, maintaining anonymity. |

## Popular Implementations

Several widely-used software solutions can function as reverse proxies:

-   **NGINX**: A high-performance, lightweight web server that is extremely popular for its robust reverse proxy and load balancing capabilities.
-   **Apache HTTP Server**: A veteran web server that can be configured as a powerful reverse proxy using its `mod_proxy` module.
-   **HAProxy**: A dedicated, high-performance open-source load balancer and proxy server for TCP and HTTP-based applications.
-   **Cloud-Native Solutions**: Major cloud providers offer managed reverse proxy and load balancing services, such as AWS Elastic Load Balancing (ELB), Google Cloud Load Balancing, and Azure Application Gateway.

## Conclusion

The reverse proxy is a critical architectural component that acts as the "front door" for modern web applications. By abstracting the backend infrastructure, it provides a unified entry point for managing traffic and enforcing policies. Its ability to deliver load balancing, enhanced security, SSL termination, and caching makes it an indispensable tool for building scalable, resilient, and high-performance web services.

