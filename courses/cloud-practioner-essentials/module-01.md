# Module 1 - Introduction to the Cloud

## What is Cloud Computing?

Cloud computing is the on-demand delivery of IT resources over the internet with pay-as-you-go pricing.

Instead of buying and maintaining physical servers, users can access computing resources whenever needed.

### Types of Cloud Computing

- Infrastructure as a Service (IaaS)
- Platform as a Service (PaaS)
- Software as a Service (SaaS)

---

## Benefits of the AWS Cloud

### Trade Capital Expense for Variable Expense

- No upfront hardware investment
- Pay only for resources used

### Benefit from Massive Economies of Scale

- AWS serves millions of customers
- Lower operational costs

### Stop Guessing Capacity

- Scale resources up or down as needed

### Increase Speed and Agility

- Provision resources in minutes

### Stop Spending Money Running Data Centers

- AWS manages infrastructure maintenance

### Go Global in Minutes

- Deploy applications worldwide quickly

---

## AWS Global Infrastructure

AWS infrastructure consists of:

### Regions

- Physical geographic locations around the world
- Example: Asia Pacific (Mumbai)

### Availability Zones (AZs)

- One or more data centers within a Region
- Designed for high availability and fault tolerance

### Edge Locations

- Used by Amazon CloudFront
- Deliver content closer to users for lower latency

---

## AWS Shared Responsibility Model

### AWS Responsibilities (Security OF the Cloud)

AWS manages:

- Physical data centers
- Networking infrastructure
- Hardware
- Virtualization layer

### Customer Responsibilities (Security IN the Cloud)

Customers manage:

- Data
- User permissions
- IAM policies
- Operating systems
- Application security

### Key Idea

AWS secures the infrastructure.
Customers secure what they deploy on AWS.

---

## Applying Cloud Concepts to Real-Life Use Cases

### Example 1: Startup Website

Traditional:
- Buy servers
- Install hardware
- High upfront cost

AWS:
- Launch EC2 instances on demand
- Scale when traffic increases

### Example 2: Data Storage

Traditional:
- Purchase storage devices

AWS:
- Store files using Amazon S3
- Pay only for storage used

### Example 3: Global Application

AWS Regions allow applications to be deployed closer to users worldwide.

---

## Important Services Mentioned

| Service | Purpose |
|----------|----------|
| EC2 | Virtual Servers |
| S3 | Object Storage |
| CloudFront | Content Delivery |
| IAM | Access Management |

---

## Revision Points

- Cloud computing provides on-demand IT resources.
- AWS uses pay-as-you-go pricing.
- Regions contain multiple Availability Zones.
- Edge Locations improve content delivery.
- AWS follows the Shared Responsibility Model.
- AWS secures the cloud, customers secure their data and applications.

---

## Interview Questions

### What is cloud computing?

On-demand delivery of IT resources over the internet with pay-as-you-go pricing.

### What is an AWS Region?

A physical geographic location containing multiple Availability Zones.

### What is an Availability Zone?

One or more isolated data centers within a Region.

### What is the Shared Responsibility Model?

AWS manages security of the cloud, while customers manage security in the cloud.

### Difference between Region and Availability Zone?

Region = Geographic location

Availability Zone = Data center(s) inside a Region