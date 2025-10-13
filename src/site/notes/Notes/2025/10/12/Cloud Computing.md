---
{"dg-publish":true,"permalink":"/notes/2025/10/12/cloud-computing/"}
---

#technology/cloud-computing
[[Cloud Computing.canvas\|Cloud Computing.canvas]]

# Cloud Computing

## 1. Introduction

**Cloud Computing** is the on-demand delivery of Information Technology (IT) resources over the internet with pay-as-you-go pricing. Instead of buying, owning, and maintaining physical data centers and servers, organizations can access technology services, such as computing power, storage, and databases, from a cloud provider like Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP).

The significance of this model lies in its fundamental shift away from the traditional capital-intensive approach of procuring IT infrastructure. Cloud computing enables organizations of all sizes to access enterprise-grade resources with minimal upfront investment, fostering unprecedented agility, scalability, and innovation. It has become the dominant paradigm for deploying new applications and is the foundational technology for trends like Big Data, the Internet of Things (IoT), and Artificial Intelligence.

## 2. The Five Essential Characteristics

The National Institute of Standards and Technology (NIST) defines cloud computing through five essential characteristics that differentiate it from traditional hosting.

1.  **On-Demand Self-Service**: A consumer can unilaterally provision computing capabilities, such as server time and network storage, as needed automatically without requiring human interaction with each service provider.
2.  **Broad Network Access**: Capabilities are available over the network and accessed through standard mechanisms that promote use by heterogeneous thin or thick client platforms (e.g., mobile phones, tablets, laptops, and workstations).
3.  **Resource Pooling**: The provider's computing resources are pooled to serve multiple consumers using a **multi-tenant** model, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand. The customer generally has no control or knowledge over the exact location of the provided resources.
4.  **Rapid Elasticity**: Capabilities can be elastically provisioned and released—in some cases automatically—to scale rapidly outward and inward commensurate with demand. To the consumer, the capabilities available for provisioning often appear to be unlimited and can be purchased in any quantity at any time.
5.  **Measured Service**: Cloud systems automatically control and optimize resource use by leveraging a metering capability. Resource usage can be monitored, controlled, and reported, providing transparency for both the provider and the consumer of the utilized service. This is the foundation of the **pay-as-you-go** model.

## 3. The Cloud Service Models

Cloud computing services are typically categorized into three main models, which represent different levels of abstraction and management.

### 3.1. Infrastructure as a Service (IaaS)
IaaS provides the most basic building blocks for cloud IT. It offers access to fundamental computing resources such as virtual machines, physical servers, storage, and networking.
-   **Analogy**: Renting the land and utilities. You are responsible for building the house, installing the plumbing, and furnishing it.
-   **User Manages**: The operating system, middleware, runtime, data, and applications.
-   **Provider Manages**: The underlying virtualization, servers, physical storage, and networking infrastructure.
-   **Examples**: Amazon Elastic Compute Cloud (EC2), Google Compute Engine, Azure Virtual Machines.

### 3.2. Platform as a Service (PaaS)
PaaS removes the need for organizations to manage the underlying infrastructure (usually hardware and operating systems) and allows them to focus on the deployment and management of their applications.
-   **Analogy**: Renting a pre-built house frame with utilities connected. You are responsible for the interior design and furnishing.
-   **User Manages**: The applications and data.
-   **Provider Manages**: The entire infrastructure stack, including the OS, middleware, and runtime environment.
-   **Examples**: Heroku, AWS Elastic Beanstalk, Google App Engine.

### 3.3. Software as a Service (SaaS)
SaaS provides a complete software product that is run and managed by the service provider. In most cases, SaaS applications are end-user applications delivered directly through a web browser.
-   **Analogy**: Renting a fully furnished and managed apartment. You simply move in and use the space.
-   **User Manages**: Nothing beyond their own user-specific settings.
-   **Provider Manages**: The entire technology stack, from the hardware to the application software itself.
-   **Examples**: Google Workspace, Microsoft 365, Salesforce.

## 4. The Cloud Deployment Models

This classification describes the environment in which the cloud services are deployed.

-   **Public Cloud**: The cloud infrastructure is provisioned for open use by the general public. It is owned, managed, and operated by a third-party cloud provider. This model offers massive economies of scale and scalability.
-   **Private Cloud**: The cloud infrastructure is provisioned for exclusive use by a single organization comprising multiple consumers (e.g., business units). It may be owned, managed, and operated by the organization, a third party, or some combination of them, and it may exist on or off-premises.
-   **Hybrid Cloud**: This model combines a private cloud with one or more public cloud services, with proprietary software enabling communication between each distinct service. It allows organizations to leverage the scalability of the public cloud for non-sensitive workloads while keeping business-critical applications and data in a secure private cloud.

## 5. The Shared Responsibility Model

A critical concept in cloud security is the **Shared Responsibility Model**. This principle defines the division of security obligations between the cloud service provider and the customer.

> The provider is responsible for the security **of** the cloud, while the customer is responsible for their security **in** the cloud.

The specific division of responsibility varies depending on the service model:
-   In **IaaS**, the customer has the most responsibility, including securing the operating system, managing network configurations, and encrypting data.
-   In **PaaS**, the provider takes on more responsibility, managing the OS and middleware, while the customer secures their applications and data.
-   In **SaaS**, the provider is responsible for securing almost the entire stack, with the customer's primary responsibility being identity and access management.

## 6. Conclusion

Cloud computing has fundamentally reshaped the landscape of information technology, transitioning it from a capital-intensive asset to a utility-based service. By offering unparalleled scalability, agility, and cost-efficiency, it has democratized access to powerful computing resources, enabling startups to compete with established enterprises and accelerating the pace of digital transformation across all industries. The continued evolution of the cloud, particularly with the rise of serverless computing, edge computing, and integrated AI/ML services, ensures that it will remain the central pillar of technological innovation for the foreseeable future.

