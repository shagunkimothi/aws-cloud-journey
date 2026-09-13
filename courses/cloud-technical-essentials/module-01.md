# Module 1 - Introduction to AWS

## What is AWS?

Amazon Web Services (AWS) is a cloud computing platform that provides on-demand IT resources over the internet.

## What is Cloud Computing?

Cloud computing is the on-demand delivery of IT resources over the internet with primarily **pay-as-you-go pricing**.

Instead of purchasing and maintaining physical hardware, users can access computing resources whenever needed.

## Cloud Deployment Models

### On-Premises

- Infrastructure is owned and managed by the organization.
- High upfront cost.
- Full control over hardware.

### Cloud

- Infrastructure is managed by a cloud provider (AWS).
- Pay only for resources used.
- Highly scalable and flexible.

### Hybrid

- Combination of on-premises and cloud infrastructure.
- Suitable for organizations migrating to the cloud.

## Advantages of Cloud Computing

- Pay as you go
- Benefit from massive economies of scale
- Stop guessing capacity
- Increase speed and agility
- Realize cost savings
- Go global in minutes

## Undifferentiated Heavy Lifting

AWS manages repetitive infrastructure tasks such as:

- Purchasing hardware
- Server maintenance
- Operating system management
- Networking
- Data center operations

This allows developers to focus on building applications.

## AWS Global Infrastructure

AWS Global Infrastructure is the worldwide network of physical data centers and networking resources that power AWS cloud services.

### Components

- Regions
- Availability Zones (AZs)
- Edge Locations

## AWS Regions

A Region is a **geographical area** where AWS hosts multiple data centers.

### Characteristics

- Independent from other Regions
- Identified by a unique Region code
- Contains multiple Availability Zones

### Examples

| Region | Region Code |
|---------|-------------|
| N. Virginia | us-east-1 |
| Tokyo | ap-northeast-1 |
| Mumbai | ap-south-1 |

### Factors for Choosing a Region

- Latency
- Pricing
- Service Availability
- Data Compliance

## Availability Zones (AZs)

An Availability Zone is **one or more data centers** within a Region.

### Characteristics

- Isolated from other AZs
- Connected with high-speed, low-latency networking
- Provides fault tolerance and high availability

### Examples

- us-east-1a
- us-east-1b
- ap-south-1a

### Best Practice

Deploy applications across **at least two Availability Zones** to improve availability and resiliency.

## Edge Locations

Edge Locations are global sites that cache content closer to users.

### Purpose

- Reduce latency
- Faster content delivery
- Improve user experience

### Example Service

- Amazon CloudFront

A website hosted in London can cache content in an Edge Location near Sydney, allowing Australian users to access content much faster.

## Scope of AWS Services

AWS services can operate at different scopes:

### Availability Zone Scope

- Resources are deployed in a specific AZ.
- Customer is responsible for high availability.

### Region Scope

- Resources are managed across the Region.
- AWS improves durability and availability automatically.

### Global Scope

- Services operate worldwide.

## Ways to Interact with AWS

AWS provides three main ways to interact with its services:

### 1. AWS Management Console

The AWS Management Console is a web-based graphical user interface (GUI) used to manage AWS resources.

**Features**

- Easy to use
- No coding required
- Suitable for beginners
- Access through a web browser

**Best For**

- Learning AWS
- Manual resource management
- Monitoring services

### 2. AWS Command Line Interface (CLI)

The AWS CLI is a command-line tool that allows users to manage AWS services by running commands in a terminal.

**Features**

- Faster than using the console
- Automates repetitive tasks
- Supports scripting
- Works on Windows, Linux, and macOS

**Example**

```bash
aws s3 ls
```

Lists all S3 buckets.

**Best For**

- Automation
- DevOps
- System administrators

### 3. AWS Software Development Kit (SDK)

AWS SDKs allow developers to interact with AWS services directly from their applications using programming languages.

**Supported Languages**

- Python (Boto3)
- Java
- JavaScript
- C#
- Go
- PHP
- Ruby

**Example (Python - Boto3)**

```python
import boto3

s3 = boto3.client('s3')
response = s3.list_buckets()
```

**Best For**

- Application development
- Backend services
- Automation within code

## Comparison

| Feature | AWS Console | AWS CLI | AWS SDK |
|----------|------------|---------|---------|
| Interface | Graphical (GUI) | Command Line | Programming APIs |
| Coding Required | No | Basic commands | Yes |
| Best For | Beginners | Automation | Application Development |

## AWS Root User

The **AWS Root User** is the account created when you first sign up for AWS. It has **full access** to all AWS services and resources.

### Root User Credentials

The root user has two types of credentials:

#### 1. Email & Password
- Used to sign in to the AWS Management Console.

#### 2. Access Keys

Used for programmatic access through:
- AWS CLI
- AWS SDK
- AWS API

Access keys consist of:
- **Access Key ID**
- **Secret Access Key**

> **Note:** Access keys should be protected like a password.

## AWS Root User Best Practices

- Use a **strong password**.
- Enable **Multi-Factor Authentication (MFA)**.
- Never share root credentials.
- Do **not** use the root user for daily tasks.
- Delete or disable root access keys if they are not required.
- Create an **IAM user** for everyday administration.

## Multi-Factor Authentication (MFA)

MFA adds an extra layer of security by requiring **two or more authentication methods**.

### Authentication Factors

| Factor | Example |
|---------|---------|
| Something you know | Password, PIN |
| Something you have | Mobile authenticator app, Security key |
| Something you are | Fingerprint, Face ID |

### How MFA Works in AWS

1. Enter email and password.
2. Enter a one-time verification code generated by an MFA device.

This helps protect your AWS account even if the password is compromised.

## Supported MFA Devices

### Virtual MFA

Authentication apps such as:
- Google Authenticator
- Microsoft Authenticator
- Authy
- Duo Mobile

### Hardware TOTP Token

- Physical device that generates one-time passwords.

### FIDO Security Key

- USB or NFC security keys (e.g., **YubiKey**).
- Provides stronger security than software-based authenticators.

## Identity and Access Management (IAM)

AWS Identity and Access Management (IAM) is a service that helps you securely manage access to AWS resources.

### Authentication vs Authorization

#### Authentication

Authentication verifies **who you are**.

Examples:
- Username and password
- Multi-Factor Authentication (MFA)

**Question:** "Who are you?"

#### Authorization

Authorization determines **what you are allowed to do** after authentication.

Examples:
- Read an S3 bucket
- Launch an EC2 instance
- Create an IAM user

**Question:** "What can you do?"

### IAM Users

An IAM User represents a single person or application that needs access to AWS.

#### Characteristics

- Has unique login credentials
- Can have passwords and access keys
- Permissions are assigned using IAM policies

#### Example

- Alice (Developer)
- Bob (Administrator)

### IAM Groups

An IAM Group is a collection of IAM users.

#### Purpose

- Simplifies permission management
- Permissions assigned to the group apply to all users in the group

#### Example

Developers Group:
- Alice
- John
- Sarah

All members inherit the same permissions.

### IAM Roles

An IAM Role is an identity with temporary permissions.

Unlike IAM users, roles do **not** have permanent credentials.

#### Common Use Cases

- EC2 accessing S3
- Lambda accessing DynamoDB
- Cross-account access
- Temporary permissions

#### Example

EC2 Instance → IAM Role → Amazon S3

### IAM Policies

IAM policies are JSON documents that define permissions.

They specify:
- Allow or Deny
- Actions
- Resources

Example:
- Allow S3 Read
- Deny EC2 Termination

### IAM Best Practices

- Never use the Root User for daily tasks.
- Enable Multi-Factor Authentication (MFA).
- Create IAM users for individuals.
- Assign permissions using IAM groups.
- Use IAM roles for AWS services and temporary access.
- Grant the least privilege required.
- Rotate access keys regularly.
- Delete unused users and credentials.

### IAM Comparison

| IAM User | IAM Group | IAM Role |
|----------|-----------|----------|
| Individual identity | Collection of users | Temporary identity |
| Permanent credentials | No credentials | Temporary credentials |
| Used by people | Permission management | AWS services & temporary access |

## Key Takeaways

- AWS is a cloud computing platform for on-demand IT resources.
- Cloud computing removes the need for large upfront infrastructure investments.
- AWS Global Infrastructure includes Regions, Availability Zones, and Edge Locations.
- AWS provides multiple ways to interact: Console, CLI, and SDK.
- The AWS Root User has full access; use IAM users and MFA for daily tasks.
- IAM lets you securely manage users, groups, roles, and policies.
- Grant the least privilege and rotate credentials regularly.

## Interview Questions

### What is IAM?

IAM is an AWS service used to securely manage access to AWS resources.

### What is the difference between authentication and authorization?

Authentication verifies identity. Authorization determines permissions.

### What is an IAM User?

An IAM User is an individual identity with permanent credentials.

### What is an IAM Role?

An IAM Role is a temporary identity used by AWS services or applications.

### Why use IAM Groups?

IAM Groups simplify permission management for multiple users.

### What is the principle of least privilege?

Grant only the permissions required to perform a specific task.

### What is the AWS Root User?

The AWS Root User is the account created during AWS registration with full access to all services.

### Why should you avoid using the root user daily?

Because it has unrestricted permissions; use IAM users with limited access instead.

### What is MFA?

Multi-Factor Authentication (MFA) adds a second verification factor to protect access.

### What are the two credentials associated with the AWS Root User?

- Email & Password
- Access Keys (Access Key ID + Secret Access Key)

### What are the cloud deployment models?

- On-Premises
- Cloud
- Hybrid

### What is undifferentiated heavy lifting?

Routine infrastructure tasks handled by AWS so developers can focus on application development.
