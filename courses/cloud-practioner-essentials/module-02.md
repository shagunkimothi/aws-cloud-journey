# Module 2 - Compute in the Cloud

## What is Compute?

Compute refers to the processing power required to run applications, process data, and perform calculations.

In cloud computing, compute resources are available on demand over the internet. Users can create and manage virtual machines without purchasing or maintaining physical hardware.

---

## Introduction to Amazon EC2

Amazon Elastic Compute Cloud (EC2) provides secure and resizable virtual servers in the AWS Cloud.

### Benefits of Amazon EC2

- Highly flexible
- Cost-effective
- Quick to launch
- Scalable
- Pay-as-you-go pricing
---
### Key Points

- EC2 provides on-demand compute capacity.
- Users can launch, scale, and terminate instances whenever needed.
- You pay only for the time your instances are running.
- EC2 instances are virtual machines (VMs).

---

## Multi-Tenancy

Multi-tenancy is the practice of sharing underlying physical hardware among multiple virtual machines.

### Characteristics

- Multiple VMs share the same physical host.
- Each VM remains isolated and secure.
- Resources are efficiently utilized.

---

## Common EC2 Use Cases

- Web applications
- Internal business applications
- Database servers
- Development and testing environments

---

## EC2 Operating Systems

EC2 instances can run:

- Linux
- Windows

---

## Scaling

### Vertical Scaling

Increase the resources of an existing instance.

Examples:

- More CPU
- More RAM
- Larger storage

Example:
- Upgrade from a t2.micro instance to a t2.large instance.
---
## Amazon EC2 Instance Types
EC2 ofers broad range of instance types each meet speific requirement . These come with varying combinator of CPU, memory, storage and networking capabilites so we can choose right to optimize performance of our application.Each EC2 instance type is grouped under an instance family.
### Types 
#### General purpose 
 A good balance of compute, memory, and networking resources. They can be used for lots of diverse workloads, like web services or code repositories. They’re also a good starting point if you don’t know how your workload will perform ahead of time.

#### Compute optimized 
 Ideal for compute-intensive tasks, like gaming servers, high-performance computing, machine learning tasks--even scientific modeling.
#### Memory optimized 
Good for memory instensive tasks. They deliver fast performance for workloads that process large data sets in memory.
#### Accelerated computing 
 Good for floating point number calculations, graphics processing, or data pattern matching. This is because they use hardware accelerators. These are co-processors that perform functions more efficiently than is possible in software running on CPUs.
#### Storage optimised
 Ideal for workloads that require high performance for locally stored data.

---
### How to provision aws resources ?
In AWS, tasks such as launching an EC2 instance, stopping an instance, or modifying instance settings are done through API requests. APIs provide predefined methods to interact with, manage, and configure AWS resources efficiently. 
#### 3 ways you can call apis 
- AWS Management console 
   - Set up test environment
   - View AWS bills
   - Work with non technical resources 
---   
- AWS CLI 
   - manage multiple AWS services from command line
   - automate tasks through scripts
---
- AWS SDK
- The AWS SDK simplifies integrating AWS services into your applications by providing APIs for various programming languages. AWS offers documentation and sample code for languages like C++, Java, and .NET to help you get started.

- Good for: Developers looking to integrate AWS services into their applications using language-specific APIs
---

## Amazon EC2 Pricing Options

### On-Demand

- Pay only for the compute capacity used.
- No long-term commitment.
- Best for short-term or unpredictable workloads.

### Savings Plans

- Commit to a consistent amount of usage.
- Lower cost compared to On-Demand pricing.
- Flexible across instance types and Regions.

### Reserved Instances

- Commit to using EC2 for 1 or 3 years.
- Significant discount compared to On-Demand pricing.
- Suitable for predictable workloads.

### Spot Instances

- Use unused AWS capacity at a discounted price.
- Can be interrupted by AWS when capacity is needed.
- Best for fault-tolerant workloads.

### Dedicated Hosts

- Physical servers dedicated to a single customer.
- Useful for licensing and compliance requirements.

### Dedicated Instances

- Instances run on hardware dedicated to a single customer.
- Provides additional isolation compared to shared tenancy.
---
| Pricing Option | Best For |
|---------------|----------|
| On-Demand | Short-term workloads |
| Savings Plans | Consistent usage with flexibility |
| Reserved Instances | Long-term predictable workloads |
| Spot Instances | Lowest cost, interruptible workloads |
| Dedicated Hosts | Licensing & compliance |
| Dedicated Instances | Additional isolation |

---
 #### Scalling Amazon EC2
 - Scalability: A system's potential to grow over time to handle an increased load by adding resources. It focuses on long-term capacity planning to accommodate more users or workloads.

- Elasticity: The ability to automatically scale resources up or down in response to real-time, fluctuating demand. It ensures cost efficiency by scaling in (shrinking) when demand decreases so you don't over-pay.
- An AWS service that automatically adds or removes EC2 instances to maintain application availability based on demand.

- Scaling Approaches:
Dynamic Scaling: Responds to real-time changes and fluctuations in demand.

- Predictive Scaling: Preemptively schedules the right number of instances based on anticipated (predicted) demand.

- Auto Scaling Group (ASG) Configurations:
An ASG is a collection of EC2 instances managed together. It requires three key capacity settings:

- Minimum Capacity: The absolute lowest number of EC2 instances required to keep the application running. The system will never scale below this threshold.

- Desired Capacity: The baseline number of EC2 instances that launch immediately when the Auto Scaling group is created.

- Maximum Capacity: The upper limit of EC2 instances the group can scale out to during peak traffic.
---
## Elastic Load Balancing (ELB)

Elastic Load Balancing (ELB) automatically distributes incoming traffic across multiple EC2 instances to improve performance, scalability, and availability.

### Key Points

- Acts as a single entry point for incoming traffic.
- Distributes requests across multiple EC2 instances.
- Improves application availability and fault tolerance.
- Works together with Amazon EC2 Auto Scaling.
- Automatically handles changes in the number of EC2 instances.

### Benefits

- Efficient traffic distribution
- Automatic scaling support
- Simplified infrastructure management
- High availability
- Better application performance

### Routing Methods

#### Round Robin
- Distributes traffic evenly across servers in a cyclic order.

#### Least Connections
- Sends traffic to the server with the fewest active connections.

#### IP Hash
- Routes requests from the same client IP to the same server.

#### Least Response Time
- Sends traffic to the server with the fastest response time.

### ELB + Auto Scaling

ELB and Auto Scaling work together:

1. ELB distributes incoming traffic.
2. Auto Scaling adds or removes EC2 instances based on demand.
3. ELB automatically starts routing traffic to new instances.

### Real-World Example

Healthcare Portal:

- Low traffic → Few EC2 instances are enough.
- High traffic → Auto Scaling launches additional instances.
- ELB distributes requests among all available instances.
- Users experience consistent performance.

---


## 1. Monoliths vs. Microservices
* **Monolithic Architecture:** Components (UI, DB, Business Logic) are **tightly coupled**. If one component fails, the entire application goes down.
* **Microservices Architecture:** Components are **loosely coupled**. If one component fails, others continue to function normally, promoting high availability and resilience.

---

## 2. AWS Messaging Services (The Decoupling Trio)
AWS uses three primary services to handle asynchronous, event-driven, and message-based communication.



### Amazon EventBridge (The Event Bus)
* **What it is:** A serverless **event bus** used to build scalable, event-driven systems.
* **How it works:** Routes events from sources (custom apps, AWS services, SaaS) to targets based on routing rules. It handles receiving, filtering, transforming, and delivering events.
* **Real-World Example (Food Delivery App):** * *Trigger:* Customer places an order.
    * *Action:* EventBridge immediately routes that single "Order Placed" event to the Payment, Restaurant, Inventory, and Delivery services simultaneously.
    * *Resilience:* If the delivery service goes down, EventBridge holds/retries the event until the service recovers.

###  Amazon SNS (Simple Notification Service - Pub/Sub)
* **What it is:** A **publish-subscribe** (Pub/Sub) messaging service.
* **How it works:** Publishers send a message to an **SNS Topic**. Multiple subscribers (Lambda, SQS, HTTP endpoints, email) listen to that topic and receive the message simultaneously.
* **Real-World Example (Targeted Company Updates):**
    * Instead of sending one massive email blast to everyone, the company creates separate SNS topics for `New Products`, `Offers`, and `Events`. Customers subscribe only to what they want.

### Amazon SQS (Simple Queue Service - Message Queue)
* **What it is:** A fully managed **message queuing** service.
* **How it works:** A producer places a message into a queue. A consumer polls the queue, retrieves the message, processes it, and then deletes it from the queue. It allows for "point-to-point" asynchronous communication.
* **Real-World Example (Customer Support Workflow):**
    * *Producer:* A support agent logs customer issues into an SQS Queue.
    * *Consumer:* A technical specialist pulls issues from the queue to fix them one by one. If the specialist is busy, the issues wait safely in the queue without being lost.

---

##  The Key Differences
* **EventBridge** is best for **routing events** based on the *content* of the event across many different services.
* **SNS** is a **fan-out** mechanism (one-to-many) pushing notifications out to many subscribers instantly.
* **SQS** is a **buffer** (one-to-one) that stores messages in a queue until a worker is ready to pull and process them.