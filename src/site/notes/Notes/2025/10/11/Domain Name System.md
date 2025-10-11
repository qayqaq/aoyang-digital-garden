---
{"dg-publish":true,"permalink":"/notes/2025/10/11/domain-name-system/"}
---

#networking #internet #dns
[[Domain Name System.canvas\|Domain Name System.canvas]]

# Domain Name System (DNS)

## Introduction

The **Domain Name System (DNS)** is a foundational protocol of the internet, often described as its "phonebook." Its primary function is to translate human-readable **domain names** (e.g., `www.wikipedia.org`) into the numerical **Internet Protocol (IP) addresses** (e.g., `208.80.154.224`) that computers use to identify each other on a network. This translation process, known as **DNS resolution**, is essential for web browsing, email, and virtually all other internet services.

DNS operates as a hierarchical and decentralized naming system. Instead of a single, massive database, the information is distributed across a global network of servers, ensuring resilience, scalability, and efficient performance. Without DNS, users would need to memorize long strings of numbers for every website they wish to visit, making the internet far less accessible.

## The Hierarchical Structure of the Domain Name Space

The DNS namespace is organized as an inverted tree structure, starting from a single root and branching out. Each node in this tree represents a domain.

-   **Root Domain (`.`)**: The top of the hierarchy, represented by a single dot. While often omitted in everyday use, it is the implicit starting point for every domain name. A name ending with a final dot, like `www.example.com.`, is called a **Fully Qualified Domain Name (FQDN)**.
-   **Top-Level Domains (TLDs)**: These are the first-level branches from the root. They are managed by the Internet Corporation for Assigned Names and Numbers (ICANN). TLDs include:
    -   **Generic TLDs (gTLDs)**: Such as `.com`, `.org`, `.net`, `.edu`.
    -   **Country Code TLDs (ccTLDs)**: Such as `.uk` (United Kingdom), `.jp` (Japan), `.de` (Germany).
-   **Second-Level Domains (SLDs)**: These are the domains registered by individuals or organizations directly under a TLD, such as `wikipedia` in `wikipedia.org`.
-   **Subdomains**: These are further subdivisions of a domain, created by the domain owner. For example, `en` in `en.wikipedia.org` is a subdomain of `wikipedia.org`.

This hierarchical structure can be formally represented as a tree graph $G = (V, E)$, where $V$ is the set of all domain labels and $E$ represents the parent-child relationships. An FQDN corresponds to a unique path from a leaf node to the root of this tree.

## Core Components of the DNS Architecture

The DNS system relies on several key components working in concert to resolve queries.

### 1. DNS Servers

There are four main types of servers involved in a typical DNS lookup:

-   **DNS Recursive Resolver (or Recursor)**: This is the server that receives the initial query from a client (e.g., your computer). It is typically operated by an Internet Service Provider (ISP) or a third-party provider (like Google's `8.8.8.8` or Cloudflare's `1.1.1.1`). The recursor is responsible for performing the full resolution process on behalf of the client.
-   **Root Name Servers**: There are 13 logical root server clusters (named A through M) distributed globally. These servers do not hold information about every domain but instead direct queries to the appropriate TLD name server.
-   **TLD Name Servers**: These servers manage all the domain names sharing a common TLD. For instance, the `.com` TLD name server holds information for all `.com` domains, pointing to the authoritative name server for each one.
-   **Authoritative Name Servers**: This is the final authority for a specific domain. It holds the definitive DNS records (e.g., the IP address) for that domain and is responsible for providing the answer to the recursive resolver.

### 2. DNS Records

Authoritative name servers store information about domains in various types of **resource records**. The most common types include:

| Record Type | | Description |
| :-- | :-- | :-- |
| **A** | | (Address) Maps a hostname to an IPv4 address. |
| **AAAA** | | (Quad A) Maps a hostname to an IPv6 address. |
| **CNAME** | | (Canonical Name) Creates an alias, mapping one domain name to another. The DNS resolution process will restart with the new name. |
| **MX** | | (Mail Exchanger) Specifies the mail servers responsible for receiving email on behalf of a domain. |
| **NS** | | (Name Server) Delegates a domain or subdomain to a set of authoritative name servers. |
| **TXT** | | (Text) Allows an administrator to store arbitrary text. Used for various purposes, including email security (SPF, DKIM) and domain ownership verification. |
| **PTR** | | (Pointer) Used for reverse DNS lookups, mapping an IP address back to a domain name. |

## The DNS Resolution Process

The process of translating a domain name into an IP address involves a sequence of queries between the different types of DNS servers. This process can be either **recursive** or **iterative**.

> A **recursive query** is one where the client asks the server to obtain the full answer on its behalf. An **iterative query** is one where the server provides the best answer it has, which may be a referral to another server.

Let's trace the steps for resolving `www.example.com`:

1.  **Client Query**: A user enters `www.example.com` into a web browser. The operating system sends a recursive query to its configured DNS recursive resolver.
2.  **Resolver Cache Check**: The resolver first checks its local cache to see if it already has the IP address for `www.example.com`. If a valid, non-expired record exists, it returns the IP immediately, and the process ends.
3.  **Iterative Query to Root Server**: If the record is not in the cache, the resolver sends an iterative query to a root name server.
4.  **Root Server Response**: The root server responds that it doesn't know the IP for `www.example.com`, but it provides the address of the TLD name server for the `.com` domain.
5.  **Iterative Query to TLD Server**: The resolver then sends an iterative query for `www.example.com` to the `.com` TLD server.
6.  **TLD Server Response**: The TLD server responds that it doesn't know the IP, but it provides the address of the authoritative name server for the `example.com` domain.
7.  **Iterative Query to Authoritative Server**: The resolver sends a final iterative query to the `example.com` authoritative name server.
8.  **Authoritative Server Response**: The authoritative server checks its records, finds the A record for `www.example.com`, and returns the corresponding IP address to the resolver.
9.  **Response to Client**: The resolver receives the IP address, stores it in its cache for a duration specified by the **Time-to-Live (TTL)** value, and returns the IP address to the client's operating system.
10. **Browser Connection**: The browser now has the IP address and can initiate a TCP connection to the web server hosting the site.

The resolution function $R$ for a domain $D$ can be modeled as a series of nested lookups:
$$
R(D) = \text{Lookup}_{\text{Authoritative}}(D, \text{Addr}(\text{NS}_{\text{TLD}}(D, \text{Addr}(\text{NS}_{\text{Root}}(D)))))
$$
where $\text{NS}_{\text{type}}(D)$ finds the name server for the relevant part of domain $D$, and $\text{Addr}(\cdot)$ retrieves its address.

## DNS Caching and Time-to-Live (TTL)

To improve performance and reduce network traffic, DNS responses are cached at multiple levels: in the browser, the operating system, and the recursive resolver. The **Time-to-Live (TTL)** is a value in a DNS record that specifies how long (in seconds) a resolver is allowed to cache that record. Once the TTL expires, the resolver must query for a fresh copy of the record.

-   **High TTL**: Reduces DNS traffic and improves lookup speed for clients but makes changes to DNS records propagate more slowly.
-   **Low TTL**: Allows for rapid changes (e.g., during a server migration) but increases the query load on authoritative name servers.

## Security in DNS

Standard DNS was designed without strong security features, leaving it vulnerable to attacks.

-   **DNS Cache Poisoning (or Spoofing)**: An attacker injects a forged DNS record into a recursive resolver's cache. When a user requests the legitimate domain, the resolver returns the attacker's malicious IP address, redirecting the user to a fraudulent site.
-   **DNS Hijacking**: An attacker maliciously modifies a computer's DNS settings or compromises a resolver to redirect all traffic to malicious servers.

To combat these threats, several security extensions have been developed:

-   **DNSSEC (Domain Name System Security Extensions)**: DNSSEC adds a layer of authenticity and integrity to DNS data. It uses digital signatures to create a chain of trust, allowing a resolver to cryptographically verify that a DNS response came from the correct authoritative server and has not been tampered with.
-   **DNS over TLS (DoT) and DNS over HTTPS (DoH)**: These protocols encrypt the DNS queries between a client and its recursive resolver. This prevents eavesdropping, manipulation, and censorship by third parties on the network path, significantly enhancing user privacy.

## Conclusion

The Domain Name System is an indispensable, yet often invisible, component of the internet's infrastructure. Its hierarchical and distributed design has allowed it to scale with the internet's explosive growth over decades. While its original design lacked robust security, the ongoing development and adoption of protocols like DNSSEC, DoT, and DoH are fortifying this critical system against modern threats. As the internet continues to evolve, DNS will remain a cornerstone technology, adapting to new challenges in security, privacy, and performance.
