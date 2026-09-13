# AWS Networking Basics


## Overview

AWS provides a wide range of networking services to build **secure, scalable, reliable, and high-performance cloud networks**.

These services help organizations:

- Build virtual networks
- Connect on-premises infrastructure to AWS
- Deliver applications globally
- Secure network traffic
- Improve application performance

---

# AWS Networking Service Categories

AWS networking services are divided into **five major categories**.

| Category | Purpose | Services |
|----------|---------|----------|
| Network Foundations | Build virtual networks | Amazon VPC, AWS Transit Gateway, AWS PrivateLink |
| Hybrid Connectivity | Connect on-premises infrastructure to AWS | AWS Direct Connect, Site-to-Site VPN, Client VPN, AWS Cloud WAN |
| Edge Networking | Deliver applications globally | Amazon CloudFront, Amazon Route 53, AWS Global Accelerator |
| Application Networking | Connect applications and microservices | AWS App Mesh, Amazon API Gateway, AWS Cloud Map |
| Network Security | Protect AWS networks | AWS Shield, AWS WAF, AWS Network Firewall, AWS Firewall Manager |

---

# 1. Network Foundations

These services create the core network infrastructure in AWS.

### Services

- Amazon VPC
- AWS Transit Gateway
- AWS PrivateLink

---

# 2. Hybrid Connectivity

Allows secure communication between on-premises infrastructure and AWS.

### Services

- AWS Direct Connect
- AWS Site-to-Site VPN
- AWS Client VPN
- AWS Cloud WAN

---

# 3. Edge Networking

Improves application performance by routing users to the nearest AWS edge location.

### Services

- Amazon CloudFront
- Amazon Route 53
- AWS Global Accelerator

---

# 4. Application Networking

Helps applications communicate securely and efficiently.

### Services

- AWS App Mesh
- Amazon API Gateway
- AWS Cloud Map

---

# 5. Networking Security

Protects applications and networks from attacks.

### Services

- AWS Shield
- AWS WAF
- AWS Network Firewall
- AWS Firewall Manager

---

# Networking on AWS

AWS networking is fully virtualized and built on the **AWS Global Network**.

Benefits include:

- High Availability
- Scalability
- Reliability
- Elasticity
- Global Connectivity

AWS networking supports different architectures, including:

- Public Networks
- Private Networks
- Hybrid Networks
- Hub-and-Spoke Networks
- Mesh Networks

---

# AWS Well-Architected Framework

AWS recommends following the **Well-Architected Framework** when designing cloud networks.

## Six Pillars

1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability

### Benefits

- Secure architectures
- High performance
- Scalability
- Cost optimization
- Resilience

---

# AWS Shared Responsibility Model

Security in AWS is a **shared responsibility** between AWS and the customer.

## AWS is Responsible For

**Security of the Cloud**

Includes:

- Physical data centers
- Hardware
- Networking infrastructure
- Regions
- Availability Zones
- Edge Locations

---

## Customer is Responsible For

**Security in the Cloud**

Includes:

- IAM configuration
- Operating systems
- Applications
- Customer data
- Network configuration
- Firewall rules
- Encryption settings

---

# Cost Optimization

AWS recommends monitoring infrastructure usage and networking costs.

Important considerations:

- Monitor data transfer charges.
- Review network usage regularly.
- Apply resource tags.
- Track expenses.

---

# AWS Cost Management Services

| Service | Purpose |
|----------|----------|
| AWS Cost Explorer | Analyze AWS spending |
| AWS Billing Console | View bills and usage |
| AWS Budgets | Set spending limits and alerts |
| AWS Trusted Advisor | Optimize cost, security, and performance |

---

# Data Transfer Pricing

### Inbound Data Transfer

 Free across all AWS Regions.

### Outbound Data Transfer

Charged based on:

- AWS Service
- AWS Region
- Destination

---

# 1. Network Foundations

Network foundations provide the core networking infrastructure for AWS workloads.

## Amazon VPC

- Creates an isolated virtual network in AWS.
- Enables complete control over networking.
- Supports subnets, route tables, and security groups.

---

## AWS Transit Gateway

- Connects multiple Amazon VPCs and on-premises networks.
- Simplifies network management.
- Uses a **hub-and-spoke** architecture.

---

## AWS PrivateLink

- Enables secure private communication between VPCs and AWS services.
- Traffic remains on the AWS network.
- No Internet Gateway, NAT Gateway, or VPN required.

---

## Benefits

- Highly scalable
- Secure networking
- Reduced operational complexity
- Cost-effective networking

---

# 2. Hybrid Connectivity

Hybrid connectivity enables secure communication between AWS and on-premises environments.

## AWS Direct Connect

- Dedicated private connection between AWS and an on-premises data center.
- Lower latency.
- Higher bandwidth.
- More consistent performance than internet-based connections.

---

## AWS Site-to-Site VPN

- Secure IPSec VPN connection.
- Connects an on-premises network to an Amazon VPC over the internet.

---

## AWS Client VPN

- Managed VPN service for individual users.
- Secure remote access to AWS and on-premises resources.

---

## AWS Cloud WAN

- Centralized service for managing global enterprise networks.
- Connects multiple AWS Regions and branch offices.

---

## Benefits

- Secure connectivity
- Global networking
- Hybrid cloud support
- Simplified management

---

# 3. Edge Networking

Edge networking improves application performance by serving users from locations close to them.

## Amazon CloudFront

- Content Delivery Network (CDN)
- Caches content at edge locations.
- Reduces latency.
- Improves website performance.

---

## Amazon Route 53

- Highly available DNS service.
- Routes users to AWS resources.
- Supports health checks and routing policies.

---

## AWS Global Accelerator

- Improves application availability and performance.
- Routes users through the AWS Global Network.
- Provides static IP addresses.

---

## Benefits

- Lower latency
- Faster content delivery
- Improved application availability
- Better user experience

---

# 4. Application Networking

Application networking services help applications communicate securely and efficiently.

## Amazon API Gateway

- Creates and manages REST and HTTP APIs.
- Integrates with Lambda and other AWS services.
- Handles authentication, throttling, and monitoring.

---

## AWS App Mesh

- Service mesh for microservices.
- Controls service-to-service communication.
- Provides observability and traffic management.

---

## AWS Cloud Map

- Service discovery solution.
- Allows applications to locate AWS resources dynamically.

---

## Benefits

- Improved scalability
- High availability
- Secure communication
- Easier service discovery

---

# 5. Network Security

Network security services protect applications and infrastructure from attacks.

## AWS Shield

- Protects against Distributed Denial of Service (DDoS) attacks.
- Shield Standard is included at no additional cost.

---

## AWS WAF

- Web Application Firewall.
- Protects web applications from common attacks such as:
  - SQL Injection
  - Cross-Site Scripting (XSS)

---

## AWS Network Firewall

- Managed firewall service for Amazon VPC.
- Filters inbound and outbound traffic.
- Supports stateful and stateless inspection.

---

## AWS Firewall Manager

- Centralized firewall management across multiple AWS accounts.
- Simplifies security policy management.

---

## Benefits

- DDoS protection
- Web application security
- Traffic filtering
- Centralized security management

---

# Shared Responsibility Model

Security in AWS is a shared responsibility.

## AWS Responsibilities

**Security of the Cloud**

- Physical infrastructure
- Global network
- Data centers
- Hardware

---

## Customer Responsibilities

**Security in the Cloud**

- IAM
- Applications
- Operating Systems
- Firewall Rules
- Data Encryption
- Network Configuration

---

# Network Design Patterns and Networking Concepts

## Overview

Designing a network requires planning for:

- High Availability
- Scalability
- Security
- Fault Tolerance
- Future Growth

AWS recommends designing networks with **no single point of failure**.

---

# Network Topologies

A network topology defines how devices communicate with each other.

## Common Network Topologies

### Point-to-Point

- Direct connection between two devices.
- Simple and fast.

---

### Bus

- All devices share one communication cable.
- Low cost but a single cable failure affects the network.

---

### Ring

- Devices form a circular path.
- Data travels around the ring.

---

### Tree

- Hierarchical structure.
- Common in enterprise networks.

---

### Hub-and-Spoke 

A central hub connects multiple networks.

```
          VPC
           │
    ┌──────┼──────┐
    │      │      │
   VPC1   VPC2   VPC3
```

**Advantages**

- Easy management
- Better scalability
- Lower complexity

Used by:

- AWS Transit Gateway

---

### Mesh

Every network connects directly to every other network.

```
A────B
│ \ / │
│ / \ │
C────D
```

**Advantages**

- High availability
- Multiple communication paths

**Disadvantages**

- Difficult to manage
- Expensive

---

### Hybrid

Combination of two or more topologies.

---

# Network Protocols

Protocols define how devices communicate.

There are three categories.

---

## 1. Network Communication Protocols

Used for data communication.

Examples:

- HTTP
- HTTPS
- FTP
- TCP/IP

---

## 2. Network Management Protocols

Used for monitoring and managing networks.

Example:

- SNMP (Simple Network Management Protocol)

---

## 3. Network Security Protocols

Protect network communications.

Examples:

- HTTPS
- TLS (Transport Layer Security)

---

# Internet Protocol (IP)

Internet Protocol (IP) enables communication between devices over a network.

There are two versions.

---

# IPv4

IPv4 uses **32-bit addresses**.

Format:

```
192.168.1.10
```

Characteristics

- Decimal notation
- Four octets
- Around **4.3 Billion** addresses

---

# IPv6

IPv6 uses **128-bit addresses**.

Format:

```
2001:0db8:85a3::8a2e:0370:7334
```

Characteristics

- Hexadecimal notation
- Much larger address space
- Improved routing
- Simpler header

---

# IPv4 vs IPv6

| IPv4 | IPv6 |
|------|------|
| 32-bit | 128-bit |
| Decimal | Hexadecimal |
| ~4.3 Billion addresses | Virtually unlimited addresses |
| Uses dotted notation | Uses colon-separated notation |

---

# Public vs Private IP

## Public IP

- Accessible from the Internet.
- Globally unique.

---

## Private IP

Used inside private networks.

Cannot communicate directly with the Internet.

Private ranges:

```
10.0.0.0/8

172.16.0.0 – 172.31.255.255

192.168.0.0/16
```

---

# NAT (Network Address Translation)

NAT converts:

```
Private IP
        │
        ▼
Public IP
```

Purpose:

- Internet access
- IP conservation
- Security

---

# CIDR (Classless Inter-Domain Routing)

CIDR allows flexible IP address allocation.

Format:

```
192.168.1.0/24
```

Where:

- 192.168.1.0 → Network Address
- /24 → Prefix Length

---

## Benefits of CIDR

- Efficient IP utilization
- Flexible subnet sizes
- Smaller routing tables

---

# Subnetting

Subnetting divides a network into smaller logical networks.

Benefits:

- Better security
- Improved performance
- Easier management
- Reduced broadcast traffic

---

# IP Address Structure

Every IP Address contains two parts.

```
Network Portion
Host Portion
```

Example

```
192.168.10.25

Network → 192.168.10

Host → 25
```

---

# Subnet Mask

A subnet mask identifies:

- Network portion
- Host portion

Example:

```
255.255.255.0
```

Purpose:

- Determines whether devices belong to the same subnet.
- Helps routers forward packets correctly.

---

# Data Storage Access

AWS provides two common storage architectures.

---

## Network Attached Storage (NAS)

Provides **file-level storage**.

AWS Services:

- Amazon EFS
- Amazon FSx

Suitable for:

- Shared file systems
- Web applications
- Content management

---

## Storage Area Network (SAN)

Provides **block-level storage**.

Characteristics:

- High speed
- Dedicated storage network
- Enterprise workloads

---

# OSI Model in AWS

## Overview

The **OSI (Open Systems Interconnection) Model** is a conceptual framework that explains how data travels across a network. It divides network communication into **seven layers**, each responsible for a specific function.

Understanding the OSI model helps in:

- Designing networks
- Troubleshooting connectivity issues
- Understanding cloud networking
- Managing AWS networking services

> In AWS, many lower-level networking tasks are abstracted because AWS manages the physical infrastructure.

---

# OSI Model

| Layer | Name | Purpose | AWS Examples |
|--------|------|---------|--------------|
| 7 | Application | Provides network services to applications | Amazon API Gateway, Amazon CloudFront, AWS App Mesh |
| 6 | Presentation | Data formatting, encryption, compression | TLS/SSL Encryption |
| 5 | Session | Establishes and maintains communication sessions | Session Management |
| 4 | Transport | Reliable end-to-end communication | Elastic Load Balancing (ELB), TCP, UDP |
| 3 | Network | Routing and IP addressing | Amazon VPC, Route Tables, Transit Gateway, Route 53 |
| 2 | Data Link | Frame delivery within a local network | Elastic Network Interface (ENI), Security Groups |
| 1 | Physical | Physical transmission of data | AWS Global Infrastructure, Data Centers, Networking Hardware |

---

# Layer 7 – Application Layer

Provides network services directly to applications.

### Responsibilities

- HTTP/HTTPS communication
- API communication
- User interaction

### AWS Services

- Amazon API Gateway
- Amazon CloudFront
- AWS App Mesh

---

# Layer 6 – Presentation Layer

Responsible for:

- Encryption
- Compression
- Data formatting

### Example

- TLS / SSL

---

# Layer 5 – Session Layer

Responsible for:

- Establishing sessions
- Maintaining sessions
- Terminating sessions

---

# Layer 4 – Transport Layer

Ensures reliable communication between systems.

### Protocols

- TCP
- UDP

### AWS Services

- Elastic Load Balancing (ELB)

Responsibilities:

- Error recovery
- Flow control
- Reliable data transfer

---

# Layer 3 – Network Layer

Responsible for routing packets between different networks.

### Responsibilities

- IP Addressing
- Routing
- Packet forwarding

### AWS Services

- Amazon VPC
- AWS Transit Gateway
- Amazon Route 53
- Route Tables

---

# Layer 2 – Data Link Layer

Transfers data between devices on the same local network.

### Responsibilities

- MAC Addressing
- Frame transmission
- Error detection

### AWS Services

- Elastic Network Interface (ENI)
- Security Groups

---

# Layer 1 – Physical Layer

Responsible for physical data transmission.

### Components

- Fiber cables
- Switches
- Routers
- Data Centers

### AWS Responsibility

AWS manages:

- Data Centers
- Servers
- Networking hardware
- Physical connectivity

---

# OSI Model in AWS

One advantage of cloud computing is that AWS abstracts many lower networking layers.

### Customer Manages

- VPC
- Security Groups
- Route Tables
- IAM
- Applications

### AWS Manages

- Physical hardware
- Data centers
- Networking equipment
- Global infrastructure

---

# Amazon VPC (Virtual Private Cloud)

## Overview

Amazon **Virtual Private Cloud (VPC)** is the foundational networking service in AWS. It enables you to create an isolated, software-defined virtual network to securely host AWS resources.

A VPC can:

- Host applications and databases
- Connect to on-premises networks
- Connect to other VPCs
- Control networking using routing and security

---

# AWS Global Infrastructure

AWS Global Infrastructure consists of:

| Component | Description |
|----------|-------------|
| Region | Geographical area containing multiple Availability Zones |
| Availability Zone (AZ) | One or more isolated data centers within a Region |
| Local Zone | Extends AWS services closer to users for low latency |
| Edge Location | Caches content using Amazon CloudFront |

---

## Resiliency Levels

### Global Services

- Replicated across multiple Regions
- Continue operating even if one Region fails

### Regional Services

- Operate within one Region
- Replicated across multiple Availability Zones

### Zone Services

- Operate within one Availability Zone
- Failure of the AZ causes service failure

---

# Amazon VPC

Amazon VPC is:

- Regional service
- Software-defined network
- Private by default
- Supports IPv4 and IPv6
- Uses CIDR blocks

---

# Types of VPC

## Default VPC

Created automatically by AWS.

Features:

- One per Region
- Public subnet in every Availability Zone
- Internet Gateway attached
- Default Route Table
- Default Network ACL
- Default Security Group

---

## Non-Default VPC

Created manually.

Features:

- Fully customizable
- Private by default
- User configures networking

---

# CIDR Block

CIDR (Classless Inter-Domain Routing) defines the IP address range of a VPC.

Example

```
10.0.0.0/16
```

All subnets inside a VPC are created from this CIDR range.

---

## Reserved IP Addresses

AWS reserves **5 IP addresses** in every subnet.

| Reserved Address | Purpose |
|------------------|---------|
| Network Address | Network identifier |
| Network +1 | VPC Router |
| Network +2 | Amazon DNS |
| Network +3 | Reserved by AWS |
| Last Address | Broadcast (Reserved) |

---

# Subnets

A subnet is a smaller network inside a VPC.

Characteristics:

- Exists in one Availability Zone
- Uses a portion of the VPC CIDR
- Can be Public or Private

---

## High Availability Best Practice

Deploy resources across multiple Availability Zones.

```
Region
│
├── AZ-A
│      └── Public Subnet
│
└── AZ-B
       └── Public Subnet
```

---

# Amazon EC2 in a VPC

EC2 instances are launched inside subnets.

Each EC2 instance receives:

- Elastic Network Interface (ENI)
- Private IP Address
- Optional Public IP

---

## Elastic IP (EIP)

Elastic IP is a static public IPv4 address.

Features:

- Persistent
- Can be moved between instances
- Charged when allocated but not attached

---

# Amazon VPC Router

Every VPC contains an AWS-managed router.

Responsibilities:

- Routes traffic between subnets
- Uses Route Tables
- Highly available

AWS manages the router automatically.

---

# Route Tables

A Route Table controls traffic flow.

Each route contains:

```
Destination → Target
```

Example

| Destination | Target |
|-------------|--------|
| 10.0.0.0/16 | Local |
| 0.0.0.0/0 | Internet Gateway |

Each subnet is associated with **one Route Table**.

---

# Internet Gateway (IGW)

Internet Gateway enables communication between a VPC and the Internet.

Features:

- Regional service
- One IGW per VPC
- Highly available

A subnet becomes **Public** only when:

- Internet Gateway is attached
- Route Table contains a route to the IGW

---

# Public vs Private Subnet

| Public Subnet | Private Subnet |
|---------------|----------------|
| Has Internet Gateway route | No Internet Gateway route |
| Internet accessible | Internal access only |

---

# Network ACL (NACL)

A Network ACL is a subnet-level firewall.

Characteristics:

- Attached to Subnets
- Stateless
- Supports Allow and Deny rules
- Rules processed in numerical order

Example

```
Internet
      │
      ▼
Network ACL
      │
      ▼
Subnet
```

---

# Security Groups

A Security Group is an instance-level firewall.

Characteristics:

- Attached to ENI
- Stateful
- Supports Allow rules only
- Automatically allows return traffic

Example

```
Internet
      │
      ▼
Security Group
      │
      ▼
EC2 Instance
```

---

# Security Group vs Network ACL

| Security Group | Network ACL |
|---------------|-------------|
| Instance Level | Subnet Level |
| Stateful | Stateless |
| Allow Only | Allow & Deny |
| Automatic return traffic | Separate inbound/outbound rules |

---

# Network Gateways

AWS provides different gateway services to connect networks.

Examples:

- Internet Gateway
- NAT Gateway
- Virtual Private Gateway
- Transit Gateway

---

# VPC Peering

VPC Peering connects **two VPCs** using private IP addresses.

Features:

- Private communication
- Supports cross-account
- Supports cross-region
- Uses AWS Global Network

Example

```
VPC A
   │
Peering
   │
VPC B
```

---

# AWS Transit Gateway

Transit Gateway acts as a **central hub** connecting multiple VPCs and on-premises networks.

Benefits:

- Simplifies routing
- Scalable architecture
- Reduces peering complexity

```
           Transit Gateway
          /      |      \
       VPC1    VPC2    VPN
```

---

# AWS PrivateLink

AWS PrivateLink enables secure private communication between:

- Amazon VPCs
- AWS Services
- On-premises networks

Traffic never traverses the public Internet.

Benefits:

- Improved security
- Private connectivity
- Simplified architecture

---

