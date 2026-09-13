# Module 3 — Exploring Compute Services

---

## 1. Unmanaged vs Managed vs Fully Managed Services

AWS services are categorized by how much responsibility the customer holds.

### 1.1 Unmanaged Services

> **Example:** Amazon EC2

| Managed By | Responsibilities |
|------------|-----------------|
| **AWS** | Physical infrastructure, data centers, hardware, networking |
| **Customer** | Operating system, security patches, network configuration, applications, data |

**Key point:** Customer has the highest level of responsibility.

---

### 1.2 Managed Services

| Managed By | Responsibilities |
|------------|-----------------|
| **AWS** | Infrastructure, maintenance, operational tasks |
| **Customer** | Service configuration, application settings, data and access control |

**Key point:** Less responsibility than unmanaged services.

---

### 1.3 Fully Managed Services

> **Example:** AWS Lambda

| Managed By | Responsibilities |
|------------|-----------------|
| **AWS** | Servers, operating systems, scaling, availability, infrastructure |
| **Customer** | Application code, permissions, data |

**Key point:** Lowest customer responsibility.

---

### 1.4 Responsibility Comparison

| Service Type | Example | Customer Responsibility |
|---|---|---|
| Unmanaged | Amazon EC2 | High |
| Managed | — | Medium |
| Fully Managed | AWS Lambda | Low |

---

### Interview Question — EC2 vs Lambda

| | Amazon EC2 | AWS Lambda |
|---|---|---|
| **Type** | Virtual machine | Serverless |
| **Management** | Customer manages OS and applications | AWS manages all infrastructure |
| **Control** | More control | Focus only on code |

---

## 2. AWS Lambda

AWS Lambda is a **serverless compute service** that runs code in response to events without requiring server management. It automatically manages the underlying infrastructure, scales resources based on request volume, and charges only for compute time consumed.

### 2.1 Use Cases

#### Image Processing
A social media application processes user-uploaded images.

- Triggered when an image is uploaded
- Resizes images and applies filters
- Stores optimized images

**Benefits:** Automatic scaling · No server management · Pay only for execution time

---

#### Personalized Content Delivery
A news aggregator recommends articles based on user preferences.

- Triggered when users open the app or search
- Fetches news from multiple sources
- Processes and returns personalized recommendations

**Benefits:** Scales automatically with traffic · Cost-effective · Event-driven execution

---

#### Real-Time Gaming Events
An online game processes player actions and leaderboard updates.

- Triggered by in-game events
- Updates player statistics and leaderboards
- Handles game state changes

**Benefits:** Real-time event processing · Handles thousands of concurrent events · No infrastructure management

---

### Why Use AWS Lambda?

- Serverless computing
- Automatic scaling
- Event-driven execution
- Pay only for usage
- No server management

---

### Interview Question — What is AWS Lambda?

AWS Lambda is a serverless compute service that runs code in response to events without requiring server management.

**Real-world use cases:** Image processing · Personalized recommendations · Real-time gaming events · File processing · Data transformation

---

## 3. Containers

### 3.1 The Deployment Problem

When a developer's local environment differs from staging or production, deployments frequently fail and are difficult to debug. Containers solve this by keeping the application environment completely consistent everywhere.

### 3.2 Containers vs Virtual Machines

| Architectural Feature | Containers | Virtual Machines (VMs) |
|---|---|---|
| **OS Footprint** | Shares the host machine's OS kernel | Runs a complete, isolated Guest OS per instance |
| **Isolation Layer** | Process-level isolation via Container Engine | Hardware-level virtualization via Hypervisor |
| **Resource Overhead** | Minimal; lightweight footprint | Significant; high CPU, RAM, and disk utilization |
| **Boot Speed** | Near-instantaneous (seconds) | Delayed (minutes) due to full OS initialization |
| **Primary Use Cases** | Microservices, scalable architectures | Full multi-tenant isolation, legacy monoliths |

---

## 4. AWS Container Services

AWS organizes its container services into three pillars.

### Pillar A — Orchestration (Cluster Managers)

| Service | Description |
|---|---|
| **Amazon ECS** (Elastic Container Service) | AWS-native, highly scalable orchestration for running Docker containers in AWS |
| **Amazon EKS** (Elastic Kubernetes Service) | Fully managed Kubernetes on AWS; no need to maintain the K8s control plane |

### Pillar B — Registry (Image Storage)

| Service | Description |
|---|---|
| **Amazon ECR** (Elastic Container Registry) | Fully managed, OCI-compliant registry to store, manage, and deploy container images |

### Pillar C — Compute (Execution Layer)

When launching ECS or EKS, you choose the underlying compute engine:

| | **Amazon EC2 Launch Type** | **AWS Fargate Launch Type** |
|---|---|---|
| **Model** | User-managed | Serverless |
| **Control** | Full server control, custom networking/hardware | Zero OS management |
| **Patching** | Manual host patching | Handled by AWS |
| **Pricing** | Pay for EC2 instances | Pay per exact vCPU/memory consumed |
| **Best for (ECS)** | SMBs needing granular infrastructure control | Agile teams with variable traffic wanting minimal ops |
| **Best for (EKS)** | Complex enterprise K8s with deep instance customization | Teams wanting Kubernetes APIs without EC2 overhead |

---

## 5. Purpose-Built Compute Services

### 5.1 Elastic Beanstalk — Platform as a Service (PaaS)

Developers upload application code (Java, .NET, Python, Node.js, PHP, Ruby, Go, or Docker); Beanstalk automatically provisions and manages the architecture.

**What AWS handles:** EC2 provisioning · Load balancing · Auto Scaling · Health checks · Network routing

**Key differentiator:** Unlike closed PaaS platforms, Beanstalk grants full root-level access to underlying AWS resources.

**Target scenarios:** RESTful APIs · Customer-facing web apps · Mobile backends · Simple microservices

---

### 5.2 AWS Batch — Large-Scale Parallel Processing

A fully managed batch computing engine that dynamically schedules and scales high-volume, asynchronous processing jobs.

**Target scenarios:**
- Scientific computing simulations
- Financial risk forecasting and quantitative trading
- Media transcoding workflows
- Big Data ETL and Machine Learning training runs
- Genomics processing and sequencing pipelines

---

### 5.3 Amazon Lightsail — Simplified Virtual Private Servers

A streamlined bundle offering VPS instances, managed databases, object storage, and networking at a **predictable flat monthly price**. Designed around a simplified point-and-click UI.

**Target scenarios:** Small business websites · WordPress blogs · Dev/test sandboxes · Lightweight line-of-business apps · Cloud-learning environments

---

### 5.4 AWS Outposts — True Hybrid Cloud Infrastructure

AWS ships physical, rack-mounted server hardware directly to your on-premises data center. This hardware runs native AWS services and APIs inside your private infrastructure, linking back to the parent AWS region.

**Target scenarios:**
- Ultra-low-latency workloads (e.g., factory floor telemetry)
- Local processing of large telemetry stores before cloud ingestion
- Strict data residency or regulatory compliance requirements
- Phased modernization of highly interconnected legacy platforms

---

## 6. Summary Cheat Sheet

| Service | Category | Exam Trigger Words |
|---|---|---|
| **Amazon ECS** | Container Orchestration | Docker containers, AWS-native, AWS ecosystem orchestration |
| **Amazon EKS** | Container Orchestration | Kubernetes, CNCF, managed K8s control plane |
| **Amazon ECR** | Container Registry | Secure image storage, OCI-compliant, Docker push/pull |
| **AWS Fargate** | Serverless Container Compute | Serverless containers, zero infrastructure, pay-per-vCPU |
| **Elastic Beanstalk** | PaaS | Upload code, automated provisioning, maintains resource control |
| **AWS Batch** | Batch Processing | Large-scale parallel jobs, dynamic scheduling, async workloads |
| **Amazon Lightsail** | VPS | Predictable pricing, simple console, small business/blog |
| **AWS Outposts** | Hybrid Infrastructure | On-premises, low latency, data residency requirements |