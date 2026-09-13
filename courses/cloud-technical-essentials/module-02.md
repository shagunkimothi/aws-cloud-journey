# Module 2- AWS Compute
# Servers

A **server** is a computer or a group of computers that provides services or resources to clients over the internet.

Servers process client requests and return appropriate responses following the **client-server model**.

---

## Client-Server Model

- **Client:** Sends a request (browser, mobile app, API client).
- **Server:** Processes the request and sends back a response.

```
Client  ─────────►  Server
(Request)          (Process Request)

Client  ◄─────────  Server
(Response)
```

---

## Responsibilities of a Server

- Process user requests
- Run applications
- Store and retrieve data
- Provide CPU, memory, and networking resources

---

## Common HTTP Servers

### Windows

- Internet Information Services (IIS)

### Linux

- Apache HTTP Server
- Nginx
- Apache Tomcat

---

# Compute Options in AWS

AWS provides three main compute options for running applications.

## 1. Virtual Machines (VMs)

- Emulates a physical server.
- Runs its own operating system.
- Provides complete control over the environment.

**AWS Service:** Amazon EC2

---

## 2. Containers

- Lightweight application environments.
- Share the host operating system.
- Faster to start than virtual machines.

**Examples:**

- Amazon ECS
- Amazon EKS

---

## 3. Serverless

- No servers to manage.
- Runs code only when triggered.
- Automatically scales.

**AWS Service:** AWS Lambda

---

# Hypervisor

A **hypervisor** is software that creates and manages virtual machines by sharing the physical hardware among multiple VMs.

### Responsibilities

- Creates virtual machines
- Allocates CPU, memory, and storage
- Isolates virtual machines

---

# Amazon EC2

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides secure and resizable virtual servers in the AWS Cloud.

### Features

- Launch virtual machines (EC2 instances)
- Scale resources as needed
- Pay only for what you use
- Supports Windows and Linux operating systems

---

# Compute Comparison

| Compute Type | AWS Service | Server Management | Best For |
|--------------|------------|-------------------|----------|
| Virtual Machine | Amazon EC2 | Customer manages OS | Traditional applications |
| Containers | Amazon ECS / EKS | Shared responsibility | Microservices |
| Serverless | AWS Lambda | AWS manages servers | Event-driven applications |

---

# Amazon EC2 - Getting Started

## Overview

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides **secure, resizable compute capacity** in the AWS Cloud. It allows users to launch virtual servers called **EC2 Instances** to run applications without purchasing physical hardware.

> **Amazon EC2 = Virtual Machine (VM) in AWS**

---

# What Can You Do with Amazon EC2?

Amazon EC2 enables you to:

- Launch virtual servers within minutes.
- Scale compute resources up or down.
- Stop, start, reboot, or terminate instances.
- Pay only for the resources you use.
- Manage instances using multiple AWS tools.

---

# Managing EC2 Instances

You can create and manage EC2 instances using:

- AWS Management Console
- AWS Command Line Interface (CLI)
- AWS SDKs
- Infrastructure as Code tools (CloudFormation)

---

# EC2 Configuration

Before launching an EC2 instance, you must configure two major categories.

## 1. Hardware Specifications

These define the physical resources allocated to the instance.

- CPU (vCPUs)
- Memory (RAM)
- Storage
- Network Performance

---

## 2. Logical Configuration

These define how the instance operates.

- Operating System
- VPC (Network)
- Security Group (Firewall)
- Key Pair (Authentication)
- Storage Configuration

---

# Amazon Machine Image (AMI)

## What is an AMI?

An **Amazon Machine Image (AMI)** is a pre-configured template used to launch an EC2 instance.

It contains:

- Operating System
- Storage Mapping
- System Architecture
- Launch Permissions
- Pre-installed Software

An EC2 instance is created from an AMI.

---

# AMI Relationship with EC2

```text
Amazon Machine Image (AMI)
            │
            ▼
Launch EC2 Instance
            │
            ▼
Running Virtual Server
```

Think of it as:

- Recipe → Cake
- Blueprint → Building
- Class → Object

The AMI defines the configuration, while the EC2 instance is the running server.

---

# Reusable AMIs

One major advantage of AMIs is **reusability**.

Example:

1. Launch an EC2 instance.
2. Install software (Apache, Nginx, Node.js, etc.).
3. Configure the application.
4. Create a new AMI from that instance.
5. Launch multiple identical EC2 instances using that AMI.

This ensures consistency across deployments.

---

# Types of AMIs

AWS provides several sources for AMIs.

## Quick Start AMIs

Official images provided by AWS.

Examples:

- Amazon Linux
- Ubuntu
- Windows Server

---

## AWS Marketplace AMIs

Pre-configured software images provided by AWS partners.

Examples:

- Jenkins
- WordPress
- MongoDB
- Docker

---

## My AMIs

Custom AMIs created by your AWS account.

---

## Community AMIs

Shared publicly by AWS users.

Use carefully, as they are not officially maintained by AWS.

---

## Custom AMIs

Images created from your own EC2 instances.

Useful for:

- Production deployments
- Backup
- Scaling identical servers

---

# AMI ID

Every AMI has a unique identifier.

Example:

```text
ami-0d5eff06f840b45e9
```

Characteristics:

- Starts with **ami-**
- Unique within an AWS Region

---

# EC2 Instance Types

An EC2 instance type defines the hardware configuration.

Example:

```text
c5n.xlarge
```

Breakdown:

| Component | Meaning |
|-----------|---------|
| c | Instance Family |
| 5 | Generation |
| n | Additional Features |
| xlarge | Instance Size |

---

# Instance Families

Different instance families are optimized for different workloads.

| Family | Best For |
|---------|-----------|
| General Purpose | Balanced workloads |
| Compute Optimized | High CPU applications |
| Memory Optimized | Databases & Analytics |
| Storage Optimized | High I/O workloads |
| Accelerated Computing | Machine Learning & Graphics |

---

# Choosing an Instance Type

Choose an instance type based on:

- CPU requirements
- Memory requirements
- Network performance
- Storage needs
- Budget

Different applications require different configurations.

---

# EC2 Networking

By default, EC2 instances launch inside the **Default VPC**.

### Default VPC

Advantages:

- Easy to get started
- Public internet access
- No manual networking configuration

Limitations:

- Not recommended for sensitive production workloads.
- Better practice is to use a custom VPC with controlled access.

---

# High Availability

High Availability ensures applications remain available even if one server fails.

### Best Practice

Deploy:

- At least **2 EC2 Instances**
- Across **2 different Availability Zones**

Example:

```text
Availability Zone A
    EC2 Instance 1

            │

Elastic Load Balancer

            │

Availability Zone B
    EC2 Instance 2
```

Benefits:

- Fault Tolerance
- Reduced Downtime
- Better Reliability

---

# Why Use Multiple Small Instances?

Instead of one large server:

```
1 Large Server
```

Use:

```
5–10 Smaller Servers
```

If one instance fails:

- Only part of the application is affected.
- Remaining instances continue serving users.

---

# EC2 Pricing

Amazon EC2 follows a **pay-as-you-go** pricing model.

Benefits:

- No upfront hardware cost
- Scale resources when needed
- Pay only while the instance is running

Minimum billing duration:

- **60 seconds**

---

# Best Practices

- Choose the correct instance type.
- Use custom AMIs for repeatable deployments.
- Launch instances inside a custom VPC for production.
- Use multiple Availability Zones.
- Scale horizontally with multiple instances.
- Stop or terminate unused instances to reduce costs.

---

# Advantages

- Highly scalable
- Secure
- Flexible instance types
- Pay-as-you-go pricing
- Fast provisioning
- Easy integration with AWS services

---

# Amazon EC2 Instance Lifecycle

## Overview

An **Amazon EC2 Instance Lifecycle** describes the different states an EC2 instance passes through from the time it is launched until it is terminated.

Understanding these states helps manage resources efficiently and optimize AWS costs.

---

# EC2 Instance Lifecycle

```text
        Launch
           │
           ▼
      Pending
           │
           ▼
       Running
      ↙    │     ↘
 Reboot  Stop   Terminate
           │
     Stopping
           │
           ▼
       Stopped
           │
        Start
           │
           ▼
       Running
```

---

# EC2 Instance States

## 1. Pending

The **Pending** state occurs immediately after launching an instance.

During this stage, AWS:

- Allocates compute resources.
- Copies the selected AMI to the root volume.
- Configures networking.
- Attaches storage.

### Billing

❌ Billing has **not started**.

---

## 2. Running

The instance is fully operational and ready for use.

You can:

- Connect via SSH/RDP
- Deploy applications
- Install software
- Reboot
- Stop
- Hibernate
- Terminate

### Billing

✅ Billing starts when the instance enters the **Running** state.

---

## 3. Reboot

Rebooting is similar to restarting a physical computer.

During reboot:

- Operating system restarts.
- Public DNS remains the same.
- Public & Private IP addresses remain unchanged.
- IPv6 address remains unchanged.
- Instance Store data remains available.

### Billing

✅ Billing continues because the instance remains running.

---

## 4. Stop

Stopping an instance is similar to shutting down a computer.

State transition:

```text
Running
   │
   ▼
Stopping
   │
   ▼
Stopped
```

When an instance is stopped:

- Compute resources are released.
- Instance can later be started again.
- May launch on different physical hardware after restart.

### Retained

- Private IPv4 Address
- IPv6 Address (if assigned)
- Amazon EBS Root Volume

### Lost

- RAM contents

### Billing

❌ Compute charges stop.

✅ EBS storage charges continue.

---

# Stop-Hibernate

Hibernate is an enhanced version of Stop.

Instead of clearing RAM, AWS saves memory contents to the **Amazon EBS Root Volume**.

```text
Running
     │
Hibernate
     │
     ▼
Stopped
```

### Benefits

- Faster startup
- Applications resume from previous state
- User sessions are preserved

### Requirements

- Hibernation must be enabled.
- Instance type must support hibernation.
- Root volume must be Amazon EBS.

---

# Stop vs Hibernate

| Feature | Stop | Stop-Hibernate |
|---------|------|----------------|
| RAM Saved | ❌ No | ✅ Yes |
| Startup Speed | Normal | Faster |
| Applications Resume | No | Yes |
| EBS Required | Yes | Yes |
| Compute Billing | Stops | Stops |

---

# 5. Terminate

Termination permanently deletes the EC2 instance.

State transition:

```text
Running
    │
Terminate
    │
    ▼
Shutting Down
    │
    ▼
Terminated
```

### After Termination

- Instance cannot be recovered.
- Instance Store data is deleted.
- Public IP is released.
- Private IP is released.
- Compute resources are removed.

### Billing

❌ Compute charges stop immediately.

---

# EC2 Pricing Options

AWS provides multiple pricing models for different workloads.

---

## 1. On-Demand Instances

Pay only for the time the instance is running.

### Best For

- Short-term workloads
- Development
- Testing
- Unpredictable traffic

### Advantages

- No upfront payment
- Flexible
- No long-term commitment

---

## 2. Spot Instances

Use unused AWS capacity at discounted prices.

### Best For

- Batch jobs
- Big Data
- CI/CD
- Fault-tolerant applications

### Advantages

- Lowest cost
- Significant discounts

### Limitation

AWS can interrupt the instance when capacity is needed.

---

## 3. Savings Plans

Commit to a consistent amount of AWS usage over a period.

### Best For

- Predictable workloads
- Long-term applications

### Benefits

- Lower cost than On-Demand
- Flexible across eligible AWS services

---

## 4. Reserved Instances

Reserve EC2 capacity for a long period.

Commitments:

- 1 Year
- 3 Years

### Best For

- Stable production workloads

### Benefits

- Significant discounts
- Capacity reservation (for some options)

---

## 5. Dedicated Hosts

A physical server dedicated to one customer.

### Best For

- Licensing requirements
- Regulatory compliance
- Security-sensitive workloads

---

# Lifecycle Billing Summary

| State | Billing |
|---------|---------|
| Pending | ❌ No |
| Running | ✅ Yes |
| Reboot | ✅ Yes |
| Stopped | ❌ Compute (EBS charged) |
| Hibernate | ❌ Compute (EBS charged) |
| Terminated | ❌ No |

---

# Best Practices

- Stop unused instances to reduce costs.
- Terminate instances that are no longer required.
- Use Hibernate for faster application recovery.
- Choose the appropriate pricing model based on workload.
- Use Spot Instances for interruptible workloads.
- Use Reserved Instances or Savings Plans for long-running applications.

---

# Container Services in AWS

## Overview

AWS provides multiple compute options to run applications. The three main categories of compute services are:

- **Virtual Machines (VMs)** – Amazon EC2
- **Containers** – Amazon ECS & Amazon EKS
- **Serverless** – AWS Lambda

There is **no one-size-fits-all** compute service. The right choice depends on your application's requirements, scalability, cost, and management needs.

---

# What are Containers?

A **container** is a standardized software package that bundles:

- Application code
- Runtime
- Libraries
- Dependencies
- Configuration files

Containers ensure that applications run **consistently across different environments**, such as development, testing, production, on-premises, and the cloud.

> **Definition:** A container packages your application and all its dependencies into a single unit that can run reliably on any platform.

---

# Why Use Containers?

Containers solve many challenges of traditional software deployment.

### Benefits

- Lightweight
- Fast startup
- Portable
- Consistent environments
- Easy deployment
- Efficient resource utilization
- Simplified application migration

---

# Common Container Workloads

Containers are commonly used for:

- Web Applications
- Microservices
- Distributed Applications
- Development & Testing Environments
- Lift-and-Shift Migrations
- CI/CD Pipelines

---

# Docker

**Docker** is one of the most popular container platforms.

It helps developers:

- Create containers
- Package applications
- Deploy applications
- Run applications consistently
- Manage networking and storage

Docker simplifies the entire container lifecycle.

---

# Virtual Machines vs Containers

| Feature | Virtual Machine (VM) | Container |
|----------|----------------------|-----------|
| Operating System | Separate OS for each VM | Shares host OS |
| Kernel | Dedicated Kernel | Shared Host Kernel |
| Startup Time | Slower | Almost Instant |
| Resource Usage | Higher | Lower |
| Portability | Moderate | High |
| Performance | Heavier | Lightweight |

---

# Architecture Comparison

## Virtual Machines

```text
Application
Operating System
Virtual Hardware
Hypervisor
Physical Server
```

Each VM has its own operating system.

---

## Containers

```text
Application
Libraries & Dependencies
Container Runtime (Docker)
Host Operating System
Physical Server
```

Multiple containers share the same operating system, making them lightweight.

---

# Container Orchestration

Running a few containers is simple.

Managing **hundreds or thousands** of containers requires automation.

This process is called **Container Orchestration**.

Container orchestration handles:

- Container deployment
- Scaling
- Scheduling
- Load distribution
- Monitoring
- Recovery from failures

---

# Challenges Without Orchestration

Managing containers manually becomes difficult because you must handle:

- Where containers should run
- Container failures
- EC2 instance failures
- Scaling applications
- Monitoring deployments
- High Availability

AWS solves these problems using orchestration services.

---

# AWS Container Services

AWS provides two managed container orchestration services:

- Amazon Elastic Container Service (Amazon ECS)
- Amazon Elastic Kubernetes Service (Amazon EKS)

---

# Amazon Elastic Container Service (Amazon ECS)

## What is Amazon ECS?

Amazon ECS is a **fully managed container orchestration service** that simplifies deploying, managing, and scaling containerized applications on AWS.

It supports:

- Docker containers
- AWS Fargate
- Amazon EC2

---

# ECS Components

## 1. Cluster

A logical group of infrastructure where containers run.

A cluster can contain:

- EC2 instances
- AWS Fargate resources

---

## 2. Task Definition

A **Task Definition** is a JSON blueprint describing how a container should run.

It specifies:

- Container Image
- CPU
- Memory
- Ports
- Networking
- Storage

Example:

```json
{
  "family": "webserver",
  "containerDefinitions": [
    {
      "name": "web",
      "image": "nginx",
      "memory": 100,
      "cpu": 99
    }
  ]
}
```

---

## 3. Task

A **Task** is a running instance of a Task Definition.

Task Definition → Task

Similar to:

Class → Object

---

## 4. Service

A Service ensures:

- Desired number of tasks remain running
- Failed tasks restart automatically
- Supports scaling
- Supports load balancing

---

# Running ECS Workloads

Amazon ECS supports two deployment options.

## Option 1 – AWS Fargate

Serverless container platform.

AWS manages:

- Servers
- Infrastructure
- Scaling

You only manage the containers.

Best for:

- Simplicity
- Small teams
- Serverless deployments

---

## Option 2 – Amazon EC2

You manage the EC2 instances yourself.

Responsibilities include:

- Provisioning servers
- Installing ECS Agent
- Scaling infrastructure
- Managing patches

Best for:

- More control
- Custom configurations
- Specialized workloads

---

# ECS Container Agent

When using EC2 launch type, each EC2 instance must have the **Amazon ECS Container Agent** installed.

Responsibilities:

- Communicates with Amazon ECS
- Reports cluster status
- Starts and stops containers
- Manages task placement

An EC2 instance with the ECS Agent installed is called a **Container Instance**.

---

# Amazon Elastic Kubernetes Service (Amazon EKS)

## What is Amazon EKS?

Amazon EKS is a **managed Kubernetes service** that allows you to run Kubernetes clusters on AWS without managing the Kubernetes control plane.

It is designed for organizations already using Kubernetes.

---

# Kubernetes

Kubernetes is an **open-source container orchestration platform** used to:

- Deploy containers
- Scale applications
- Manage workloads
- Recover failed containers
- Automate deployments

---

# ECS vs EKS Terminology

| Amazon ECS | Amazon EKS |
|-------------|------------|
| Task | Pod |
| Container Instance | Worker Node |
| ECS Agent | Kubernetes Components |
| AWS Native | Kubernetes |

---

# ECS vs EKS

| Feature | Amazon ECS | Amazon EKS |
|----------|------------|------------|
| Platform | AWS Native | Kubernetes |
| Complexity | Simple | More Advanced |
| Management | Easier | More Flexible |
| Best For | AWS-based applications | Existing Kubernetes workloads |

---

# When to Choose ECS

Choose Amazon ECS when:

- Building applications on AWS
- Using Docker containers
- You want simple container orchestration
- Tight integration with AWS services is required

---

# When to Choose EKS

Choose Amazon EKS when:

- Already using Kubernetes
- Need Kubernetes portability
- Require advanced orchestration features
- Running multi-cloud Kubernetes workloads

---

# Best Practices

- Use **AWS Fargate** for serverless container deployments.
- Use **Amazon ECS** for simple AWS-native container orchestration.
- Use **Amazon EKS** if your organization already relies on Kubernetes.
- Use container orchestration for high availability and automatic scaling.
- Define containers using Task Definitions for consistent deployments.

---

# Advantages

- Fast deployment
- Lightweight applications
- Consistent environments
- High scalability
- High availability
- Efficient resource utilization
- Simplified container management

---

# Serverless with AWS Fargate

## Overview

**AWS Fargate** is a **serverless compute engine for containers** that allows you to run containerized applications without provisioning or managing servers.

It works with both **Amazon Elastic Container Service (Amazon ECS)** and **Amazon Elastic Kubernetes Service (Amazon EKS)**.

> **Definition:** AWS Fargate is a purpose-built serverless compute engine that automatically manages the infrastructure required to run containers.

---

# Why AWS Fargate?

Traditionally, when running containers on Amazon ECS or Amazon EKS using EC2, you are responsible for:

- Launching EC2 instances
- Managing cluster capacity
- Scaling infrastructure
- Patching operating systems
- Monitoring server health

AWS Fargate removes these responsibilities by automatically managing the underlying compute infrastructure.

---

# How AWS Fargate Works

```text
Application
      │
Container
      │
Amazon ECS / Amazon EKS
      │
AWS Fargate
      │
AWS Infrastructure
```

With Fargate:

- Developers deploy containers.
- AWS automatically provisions and manages the compute resources.
- No EC2 instances need to be managed.

---

# Key Features

## 1. Serverless Compute

No servers to provision or maintain.

AWS automatically handles:

- Infrastructure
- Compute resources
- Server management

---

## 2. Automatic Scaling

AWS Fargate automatically allocates the required compute resources based on the workload.

Benefits:

- No manual scaling
- Better resource utilization
- Simplified operations

---

## 3. Pay-as-You-Go Pricing

You pay only for the compute resources used by your running containers.

Benefits:

- No payment for idle EC2 instances
- Cost-effective for variable workloads

---

## 4. Supports Amazon ECS and Amazon EKS

AWS Fargate can be used with:

- Amazon ECS
- Amazon EKS

This provides flexibility to use either AWS-native container orchestration or Kubernetes.

---

## 5. Native AWS Integration

AWS Fargate integrates seamlessly with AWS services such as:

- AWS Identity and Access Management (IAM)
- Amazon Virtual Private Cloud (Amazon VPC)

These integrations provide secure access control and networking for containerized applications.

---

## 6. Improved Security

AWS Fargate provides workload isolation by design.

Benefits include:

- Better security
- Isolated container execution
- Reduced infrastructure management

---

# AWS Fargate and Amazon VPC

AWS Fargate integrates with **Amazon VPC**, allowing containers to run within your private network.

This enables you to:

- Launch containers inside your VPC
- Control inbound and outbound traffic
- Secure application connectivity using VPC networking

---

# AWS Fargate vs Amazon ECS on EC2

| Feature | Amazon ECS on EC2 | AWS Fargate |
|----------|-------------------|-------------|
| Manage EC2 Instances | ✅ Yes | ❌ No |
| Server Management | Required | AWS Managed |
| Infrastructure Scaling | Manual | Automatic |
| Pay for Idle Servers | Yes | No |
| Container Orchestration | Amazon ECS | Amazon ECS / Amazon EKS |

---

# Benefits of AWS Fargate

- No server management
- Automatic infrastructure scaling
- Simplified container deployment
- Pay-as-you-go pricing
- Native integration with IAM and Amazon VPC
- Improved workload isolation and security
- Compatible with both Amazon ECS and Amazon EKS

---

# Use Cases

AWS Fargate is suitable for:

- Microservices
- Web applications
- Containerized APIs
- Event-driven applications
- Applications with variable workloads
- Teams that want to focus on application development instead of infrastructure management

---

# Best Practices

- Use AWS Fargate when you want to avoid managing EC2 instances.
- Integrate containers with Amazon VPC for secure networking.
- Use IAM roles to securely control access to AWS resources.
- Choose Fargate for workloads requiring automatic scaling and simplified operations.

---

# Advantages

- Fully serverless container compute
- No infrastructure management
- Automatic scaling
- Secure workload isolation
- Cost-efficient pay-as-you-go pricing
- Supports both Amazon ECS and Amazon EKS

---

# Serverless with AWS Lambda

## Overview

**AWS Lambda** is a **serverless compute service** that allows you to run code without provisioning or managing servers. AWS automatically handles the infrastructure, scaling, availability, and execution of your code.

> **Definition:** AWS Lambda is a serverless service that executes your code in response to events without requiring server management.

---

# Why AWS Lambda?

Traditionally, running an application requires managing:

- Servers
- Operating Systems
- Scaling
- Availability
- Patching
- Infrastructure

With AWS Lambda:

- No servers to manage
- Automatic scaling
- High availability
- Pay only for execution time

Developers focus only on writing application code.

---

# Common Use Cases

AWS Lambda can be used for:

- Data Processing
- Real-time Stream Processing
- Machine Learning Workloads
- Web Applications
- REST APIs
- WebSocket Applications
- Mobile Backends
- IoT Backends
- Backend Services

---

# How AWS Lambda Works

```text
Event
   │
   ▼
Trigger
   │
   ▼
Lambda Function
   │
   ▼
Process Code
   │
   ▼
Return Response
```

A Lambda function runs only when it is triggered by an event.

---

# Lambda Function

A **Lambda Function** is the core component of AWS Lambda.

It contains:

- Application code
- Business logic
- Configuration
- Runtime settings

A function performs a specific task whenever it is invoked.

---

# Function Invocation

A Lambda function can be invoked in two ways:

### Direct Invocation

Using:

- AWS Lambda API
- AWS Management Console
- AWS SDK
- AWS CLI

---

### Event-Based Invocation

An AWS service automatically triggers the function when an event occurs.

Examples:

- File uploaded to Amazon S3
- HTTP request through Amazon API Gateway
- Database update
- Scheduled event
- CloudWatch Event

---

# Core Lambda Concepts

## 1. Function

The executable code that performs a task.

---

## 2. Trigger

The AWS service or resource that starts the Lambda function.

Examples:

- Amazon S3
- Amazon API Gateway
- Amazon EventBridge
- Amazon DynamoDB

---

## 3. Event

The data passed to the Lambda function when it is triggered.

Example:

An S3 upload event contains:

- Bucket name
- File name
- Timestamp

---

## 4. Application Environment

The execution environment where the Lambda function runs.

AWS automatically provisions and manages this environment.

---

## 5. Deployment Package

The package uploaded to Lambda containing:

- Source Code
- Dependencies
- Libraries

---

## 6. Runtime

The programming language environment used to execute the function.

AWS Lambda supports multiple runtimes, such as:

- Python
- Java
- Node.js
- C#
- Go
- Ruby

---

## 7. Lambda Function Handler

The **Handler** is the entry point of the Lambda function.

It receives:

- Event
- Context

And executes the application logic.

---

# AWS Lambda Configuration

Lambda functions can be created and managed using:

- AWS Management Console
- AWS Lambda API
- AWS CloudFormation
- AWS Serverless Application Model (AWS SAM)

---

# Automatic Scaling

AWS Lambda automatically scales based on incoming requests.

Example:

```text
1 Request
     │
1 Lambda Instance

1000 Requests
     │
1000 Concurrent Lambda Executions
```

No manual scaling is required.

---

# High Availability

Lambda runs on AWS managed infrastructure.

AWS automatically provides:

- High Availability
- Fault Tolerance
- Resource Management

No additional configuration is required.

---

# Pricing

AWS Lambda uses a **pay-for-use** pricing model.

You are charged based on:

## 1. Number of Requests

Every invocation counts as one request.

---

## 2. Execution Duration

Billing is based on the execution time of the function.

- Measured in **milliseconds (ms)**
- Rounded up to the nearest **1 ms**

There is **no minimum runtime**.

This makes Lambda highly cost-effective for short-running functions.

---

# AWS Lambda Advantages

- No server management
- Automatic scaling
- High availability
- Built-in fault tolerance
- Millisecond billing
- Cost-effective
- Easy integration with AWS services

---

# Lambda vs Amazon EC2

| Feature | Amazon EC2 | AWS Lambda |
|----------|------------|------------|
| Server Management | Required | Not Required |
| Infrastructure | User Managed | AWS Managed |
| Scaling | Manual / Auto Scaling | Automatic |
| Billing | Running Instance Time | Requests + Execution Time |
| High Availability | User Configures | Built-in |

---

# Lambda vs AWS Fargate

| Feature | AWS Lambda | AWS Fargate |
|----------|------------|-------------|
| Executes | Individual Functions | Containers |
| Server Management | None | None |
| Best For | Event-driven applications | Containerized applications |
| Scaling | Automatic | Automatic |

---

# Best Practices

- Keep Lambda functions small and focused on a single task.
- Use event-driven architecture whenever possible.
- Package only the required dependencies.
- Monitor function performance and execution time.
- Choose Lambda for short-lived, event-based workloads.

---

# Advantages

- Fully serverless
- No infrastructure management
- Automatic scaling
- High availability
- Millisecond billing
- Cost-efficient
- Fast deployment
- Supports multiple programming languages

---

