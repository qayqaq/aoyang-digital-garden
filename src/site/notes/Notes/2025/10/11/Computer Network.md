---
{"dg-publish":true,"permalink":"/notes/2025/10/11/computer-network/"}
---

#computer-science/networking

[[Computer Network.canvas\|Computer Network.canvas]]

# Computer Network

## 1. Introduction to Computer Networks

A **computer network** is a collection of interconnected computing devices that can exchange data and share resources. These devices, known as **nodes**, are connected via communication channels, or **links**. The primary significance of computer networks lies in their ability to facilitate communication, enable resource sharing (such as printers and files), and provide access to vast amounts of information, most notably through the Internet.

The functioning of any computer network is governed by a set of rules called **protocols**, which define the syntax, semantics, and synchronization of communication. Without these standardized protocols, devices from different manufacturers would be unable to understand one another, rendering the network useless.

## 2. Fundamental Components

Every computer network, regardless of its size or complexity, is built upon three fundamental components.

### 2.1. Nodes and Hosts
A **node** is any device connected to the network that is capable of sending, receiving, or forwarding information. Examples include:
-   **Hosts** or **End Devices**: Computers, servers, smartphones, and IoT devices where applications run.
-   **Intermediary Devices**: Switches, routers, and hubs that connect hosts and manage data flow.

### 2.2. Links (Communication Media)
A **link** is the physical or wireless medium used to transmit data between nodes. Links are characterized by their **bandwidth** (the maximum rate of data transfer) and **latency** (the delay in data transmission).
-   **Wired Media**: Includes Ethernet cables (Twisted Pair), coaxial cables, and fiber-optic cables, offering high speed and reliability.
-   **Wireless Media**: Utilizes radio waves to transmit data, as seen in Wi-Fi (WLAN), Bluetooth (WPAN), and Cellular networks (WWAN).

### 2.3. Protocols
A **protocol** is a formal set of rules and conventions that governs how data is formatted, transmitted, and received. It ensures orderly and reliable communication. The most foundational protocol suite for the internet is **TCP/IP (Transmission Control Protocol/Internet Protocol)**.

> Think of protocols as the grammatical rules of a language. For two people to communicate effectively, they must speak the same language and follow its rules. Similarly, for two devices to communicate, they must use the same protocols.

## 3. Network Topologies

**Network topology** refers to the physical or logical arrangement of nodes and links in a network. The choice of topology affects the network's performance, scalability, and fault tolerance.

-   **Bus Topology**: All nodes are connected to a single central cable, called the bus. It is simple to install but vulnerable, as a failure in the main cable disrupts the entire network.
-   **Star Topology**: All nodes are connected to a central device (a hub or switch). It is easy to manage and a failure in one link does not affect others, but a failure of the central device brings down the network.
-   **Ring Topology**: Each node is connected to exactly two other nodes, forming a single continuous pathway for signals through each node—a ring. Data travels in one direction.
-   **Mesh Topology**: Every node is connected to every other node (full mesh) or to several other nodes (partial mesh). This provides high redundancy and reliability but is expensive and complex to implement.
-   **Hybrid Topology**: A combination of two or more different topologies.

## 4. Network Architecture and Layered Models

Network architecture describes the design of a computer network. To manage the complexity of network communication, architects use layered models, which divide the task into a series of smaller, manageable functions, or layers.

### 4.1. The OSI Model
The **Open Systems Interconnection (OSI) Model** is a conceptual framework that standardizes the functions of a telecommunication or computing system into seven abstract layers.

1.  **Layer 7: Application**: The human-computer interaction layer, where applications can access the network services. (e.g., HTTP, FTP, SMTP).
2.  **Layer 6: Presentation**: Ensures that data is in a usable format and is where data encryption occurs.
3.  **Layer 5: Session**: Manages and terminates connections between applications.
4.  **Layer 4: Transport**: Provides reliable or unreliable delivery and error correction before retransmission. (e.g., TCP, UDP).
5.  **Layer 3: Network**: Responsible for packet forwarding, including routing through different routers. (e.g., IP).
6.  **Layer 2: Data Link**: Responsible for node-to-node data transfer and error detection from the physical layer. (e.g., Ethernet, MAC Addresses).
7.  **Layer 1: Physical**: The physical equipment involved in data transfer, such as cables and switches.

### 4.2. The TCP/IP Model
The **TCP/IP Model** is a more practical, four-layered model that is the foundation of the modern Internet. It is less prescriptive than the OSI model but describes the functions required for successful communication.

1.  **Application Layer**: Combines the OSI Application, Presentation, and Session layers.
2.  **Transport Layer**: Corresponds to the OSI Transport layer.
3.  **Internet Layer**: Corresponds to the OSI Network layer.
4.  **Network Access (or Link) Layer**: Combines the OSI Data Link and Physical layers.

## 5. Classification by Scale

Networks are often classified by their geographical scope.

-   **PAN (Personal Area Network)**: Spans a very short distance, typically for connecting personal devices like a mouse, keyboard, or smartphone. (e.g., Bluetooth).
-   **LAN (Local Area Network)**: Covers a limited area such as a home, office, or school. (e.g., Ethernet, Wi-Fi).
-   **MAN (Metropolitan Area Network)**: Spans a physical area larger than a LAN but smaller than a WAN, such as a city.
-   **WAN (Wide Area Network)**: Covers a broad geographical area, such as a country or continent. The **Internet** is the largest WAN.

## 6. Mathematical Foundations of Networking

Several key performance metrics and theoretical limits in networking are defined by mathematical principles.

### 6.1. Latency and Throughput
-   **Throughput** is the actual rate at which data is successfully transferred through a channel. It is always less than or equal to the channel's **bandwidth**, which is the theoretical maximum rate.
-   **Latency** (or delay) is the total time it takes for a data packet to travel from its source to its destination. It is the sum of several components:
    $$
    T_{\text{latency}} = T_{\text{propagation}} + T_{\text{transmission}} + T_{\text{queuing}} + T_{\text{processing}}
    $$
    Where:
    -   $T_{\text{propagation}}$ is the time for a bit to travel the length of the link.
    -   $T_{\text{transmission}}$ is the time to push all the packet's bits onto the link.
    -   $T_{\text{queuing}}$ is the time the packet spends in router queues.
    -   $T_{\text{processing}}$ is the time taken by a router to process the packet header.

### 6.2. Shannon-Hartley Theorem
This theorem establishes the theoretical maximum data rate, or **channel capacity** ($C$), for a communication channel with a specific bandwidth ($B$) and signal-to-noise ratio ($S/N$). It provides an upper bound on the rate of error-free communication.

The formula is:
$$
C = B \log_2(1 + S/N)
$$
Where:
-   $C$ is the channel capacity in bits per second (bps).
-   $B$ is the bandwidth of the channel in Hertz (Hz).
-   $S/N$ is the signal-to-noise power ratio (a linear power ratio, not in decibels).

This theorem highlights a fundamental trade-off: to increase data rate, one must either increase the bandwidth or improve the signal quality relative to the noise.

## 7. Conclusion

Computer networks are the backbone of the digital world, enabling everything from simple file sharing to global-scale cloud computing. Understanding their fundamental components—nodes, links, and protocols—as well as their structure through topologies and layered architectures like OSI and TCP/IP, is essential for comprehending modern technology. As networking evolves with advancements like 5G, the Internet of Things (IoT), and software-defined networking (SDN), these core principles will continue to provide the foundation for innovation in communication and connectivity.

