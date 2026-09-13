# AWS Lambda Foundations
# Introduction to Serverless

## What is Serverless?

Serverless computing is a cloud computing model where AWS manages the underlying infrastructure, allowing developers to focus only on writing and deploying code.

In a serverless environment, there are **no servers, operating systems, or instances to manage**.

---

## Traditional vs Serverless

| Task | Traditional Environment | Serverless |
|------|--------------------------|------------|
| Configure servers | ✅ Yes | ❌ No |
| Update Operating System | ✅ Yes | ❌ No |
| Install application platform | ✅ Yes | ❌ No |
| Build & Deploy Applications | ✅ Yes | ✅ Yes |
| Configure Auto Scaling & Load Balancing | ✅ Yes | ❌ No |
| Monitor Infrastructure | ✅ Yes | ❌ No |
| Monitor Applications | ✅ Yes | ✅ Yes |

### Key Idea

AWS manages the infrastructure, while developers focus on application development.

---

# AWS Serverless Platform

AWS provides several fully managed services for building serverless applications.

| Category | AWS Service |
|----------|-------------|
| Compute | AWS Lambda, Lambda@Edge |
| Orchestration | AWS Step Functions |
| Storage | Amazon S3 |
| Database | Amazon DynamoDB |
| Event Bus | Amazon EventBridge |
| Messaging | Amazon SNS, Amazon SQS |
| API Integration | Amazon API Gateway, AWS AppSync |
| Developer Tools | AWS CDK, AWS SAM |

---

# AWS Lambda

AWS Lambda is a **serverless compute service** that runs code without provisioning or managing servers.

AWS automatically handles:

- Infrastructure
- Server management
- Operating system
- Capacity provisioning
- Automatic scaling
- Monitoring
- Logging

---

## Benefits of AWS Lambda

- No server management
- Event-driven execution
- Automatic scaling
- High availability
- Built-in monitoring and logging
- Pay only when your code runs

---

# Features of AWS Lambda

- Run code without provisioning servers.
- Executes functions in response to events.
- Automatically scales based on workload.
- Built-in monitoring through Amazon CloudWatch.
- Supports multiple programming languages.
- High availability.

---

# Event-Driven Architecture

An **event-driven architecture** executes actions whenever an event occurs.

An **event** is any change in state, user action, or system update.

### Examples of Events

- Image uploaded to Amazon S3
- User places an order
- Database record updated
- New message received in Amazon SQS

---

## Components of Event-Driven Architecture

### Producer

Generates events.

Examples:

- Amazon S3
- DynamoDB
- SNS
- EventBridge

↓

### Event Router

Routes events to the appropriate service.

↓

### Consumer

Processes the event.

Example:

- AWS Lambda Function

---

# Lambda Function

A Lambda Function is the code that runs on AWS Lambda.

### Characteristics

- Small and self-contained
- Stateless
- Event-driven
- Automatically scales
- Executes only when triggered

---

## Common Event Sources

- Amazon S3
- Amazon DynamoDB Streams
- Amazon Kinesis
- Amazon SNS
- Amazon EventBridge

---

# AWS Lambda Workflow

```text
Event Occurs
      │
      ▼
Event Source (S3, SNS, DynamoDB)
      │
      ▼
AWS Lambda
      │
      ▼
Execute Function
      │
      ▼
Return Result
```

---

# Key Takeaways

- Serverless removes infrastructure management.
- AWS Lambda is a serverless compute service.
- Lambda runs code only when triggered.
- Lambda automatically scales.
- Lambda integrates with many AWS services.
- Event-driven architectures improve scalability and flexibility.

---

# AWS Lambda Invocation Models

Lambda functions can be invoked using **three invocation models**.

---

## 1. Synchronous Invocation

The caller waits for the Lambda function to finish execution and receive a response.

### Characteristics

- Immediate response
- No automatic retries
- Suitable for real-time applications

### Examples

- Amazon API Gateway
- Application Load Balancer (ALB)
- Amazon Alexa

---

## 2. Asynchronous Invocation

The event source sends the event to Lambda and continues without waiting for a response.

### Characteristics

- Event queued internally
- Automatic retries (up to **2 retries**)
- Best for background processing

### Examples

- Amazon S3
- Amazon SNS
- Amazon EventBridge

---

## 3. Polling Invocation

Lambda continuously polls an event source for new messages.

### Characteristics

- Lambda polls the event source
- Retry behavior depends on the event source
- Used for stream and queue processing

### Examples

- Amazon SQS
- Amazon DynamoDB Streams
- Amazon Kinesis

---

# Invocation Model Comparison

| Invocation Model | Waits for Response | Retry Behavior | Examples |
|------------------|-------------------|----------------|----------|
| Synchronous | Yes | No retries | API Gateway, ALB, Alexa |
| Asynchronous | No | Retries twice | S3, SNS, EventBridge |
| Polling | No | Depends on event source | SQS, DynamoDB Streams, Kinesis |

---

# Error Handling

| Invocation Model | Error Behavior |
|------------------|---------------|
| Synchronous | No retries |
| Asynchronous | Automatic retries (2) |
| Polling | Depends on event source |

---

# AWS Lambda Execution Environment

Lambda executes functions inside a secure and isolated **Execution Environment**.

It manages:

- Runtime
- Memory
- CPU
- Environment variables
- Credentials
- Extensions

---

# Lambda Lifecycle

## 1. Init Phase

- Lambda creates the execution environment.
- Initializes runtime.
- Loads function code.
- Runs initialization code.

---

## 2. Invoke Phase

- Event source invokes the function.
- Lambda executes the handler code.
- Returns the response.

---

## 3. Shutdown Phase

- Lambda shuts down the runtime.
- Releases resources when no longer required.

---

# Cold Start

A **Cold Start** occurs when Lambda creates a **new execution environment**.

### Causes

- First invocation
- Function update
- Increased concurrent requests
- Long idle period

### Disadvantage

- Increased latency

---

# Warm Start

A **Warm Start** occurs when Lambda reuses an existing execution environment.

### Advantages

- Faster execution
- Lower latency
- No initialization required

---

# Provisioned Concurrency

Provisioned Concurrency keeps Lambda execution environments **initialized and ready** before requests arrive.

### Benefits

- Reduces cold starts
- Predictable low latency
- Better performance for real-time applications

---

# Best Practices

- Store dependencies outside the handler.
- Reuse existing database connections.
- Avoid unnecessary variable initialization.
- Use `/tmp` storage for temporary caching.
- Use Provisioned Concurrency for latency-sensitive applications.

---

# AWS Lambda Permissions

AWS Lambda uses **two types of IAM policies** to control security and access.

1. Resource-Based Policy
2. Execution Role

---

# 1. Execution Role

An **Execution Role** defines **what a Lambda function is allowed to do** after it has been invoked.

Lambda automatically assumes this role when the function executes.

## Purpose

Allows Lambda to access other AWS services.

### Examples

- Read from Amazon S3
- Write to DynamoDB
- Publish messages to Amazon SNS
- Send logs to Amazon CloudWatch

---

## Components of an Execution Role

### IAM Policy

Defines the permissions granted to the Lambda function.

Example:

- Read S3
- Write DynamoDB
- Publish SNS messages

---

### Trust Policy

Allows AWS Lambda to assume the execution role.

The trust policy includes the **AssumeRole** permission.

---

## Best Practices

- Follow the **Principle of Least Privilege**.
- Grant only the permissions required.
- Avoid using AdministratorAccess.
- Remove unused permissions.

---

# Principle of Least Privilege

Grant only the minimum permissions required for the Lambda function to perform its task.

Example:

Instead of giving full S3 access:

❌ AmazonS3FullAccess

Use:

✅ Read access to only the required bucket.

---

# IAM Access Analyzer

IAM Access Analyzer helps generate IAM policies based on the permissions actually used by your Lambda function.

Benefits:

- Reduces unnecessary permissions
- Improves security
- Simplifies policy creation

---

# 2. Resource-Based Policy

A **Resource-Based Policy** defines **who is allowed to invoke the Lambda function**.

It specifies which users, services, roles, or AWS accounts can trigger the function.

---

## Purpose

Controls who can execute the Lambda function.

---

## Examples

- Amazon S3 triggers Lambda
- Amazon API Gateway invokes Lambda
- EventBridge invokes Lambda
- Another AWS Account invokes Lambda

---

## Common Use Cases

- Cross-account access
- Service integrations
- Event sources

---

# Resource Policy vs Execution Role

| Resource-Based Policy | Execution Role |
|------------------------|----------------|
| Controls **who can invoke Lambda** | Controls **what Lambda can do** |
| Attached to the Lambda Function | Attached to the IAM Role |
| Used by event sources | Used during function execution |
| Example: S3 invokes Lambda | Example: Lambda writes to DynamoDB |

---

# Cross-Account Access

Resource policies allow AWS resources from another AWS account to invoke a Lambda function.

Example:

```
AWS Account A
      │
      ▼
Invoke Lambda
      │
      ▼
AWS Account B
```

---

# AWS SAM

AWS Serverless Application Model (SAM) simplifies:

- Lambda deployment
- IAM policy creation
- Infrastructure management

---

# Lambda in a VPC

A Lambda function can access resources inside a Virtual Private Cloud (VPC).

Required:

- VPC
- Subnets
- Security Groups
- Execution Role with **AWSLambdaVPCAccessExecutionRole**

---

# AWS PrivateLink

AWS PrivateLink enables private communication between a VPC and Lambda APIs.

Benefits:

- No Internet Gateway required
- No NAT Gateway required
- Traffic remains inside the AWS network

---

# Key Takeaways

- Lambda uses **Execution Roles** and **Resource Policies**.
- Execution Role controls **what Lambda can do**.
- Resource Policy controls **who can invoke Lambda**.
- Always follow the Principle of Least Privilege.
- Use IAM Access Analyzer to create secure policies.
- AWS SAM simplifies IAM policy management.

---

# Memory Trick

```
Execution Role
"What can I do?"

Lambda
   │
   ▼
S3
DynamoDB
SNS
CloudWatch
```

```
Resource Policy
"Who can call me?"

S3
API Gateway
EventBridge
Another AWS Account
        │
        ▼
      Lambda
```

---

# AWS Lambda Programming Model

## Supported Programming Languages

AWS Lambda supports multiple programming languages:

- Node.js
- Python
- Java
- Go
- C#
- Ruby
- PowerShell

AWS also supports **Custom Runtimes**.

---

## Supported IDEs

- Visual Studio Code (VS Code)
- IntelliJ IDEA
- Eclipse
- PyCharm

---

# Lambda Handler

The **Handler** is the entry point of a Lambda function.

Whenever Lambda invokes a function, it starts execution from the handler.

## Handler Parameters

### Event Object

Contains information about the event that triggered the function.

Examples:

- S3 object upload
- API Gateway request
- SNS message

---

### Context Object

Provided by AWS.

Contains metadata such as:

- Request ID
- Remaining execution time
- Function name
- Memory limit

---

# Lambda Function Best Practices

## 1. Separate Business Logic

Keep business logic separate from the handler.

### Benefits

- Easier testing
- Better code reuse
- Cleaner code

---

## 2. Write Modular Functions

Each Lambda function should perform **one specific task**.

Example:

Instead of one function:

- Resize Image
- Compress Image
- Store Image

Use three separate Lambda functions.

---

## 3. Treat Functions as Stateless

Do not store application state inside Lambda.

Every invocation should be independent.

---

## 4. Include Only What You Need

Package only the required code and dependencies.

Smaller deployment packages improve performance.

---

# Coding Best Practices

- Include logging statements.
- Return meaningful responses.
- Use environment variables for configuration.
- Store secrets securely (AWS Secrets Manager or Parameter Store).
- Avoid recursive function calls.
- Monitor with Amazon CloudWatch.
- Reuse execution context whenever possible.

---

# Ways to Build Lambda Functions

AWS provides three methods.

## 1. Lambda Console

Best for:

- Beginners
- Learning
- Small applications
- No external libraries

### Create Function Options

- Author from Scratch
- Use Blueprint
- Use Container Image

---

## 2. Deployment Packages

Deploy using:

- ZIP Archive
- Container Image

Container images are stored in:

- Amazon Elastic Container Registry (Amazon ECR)

---

## 3. Automation Tools

Used for professional deployments.

Examples:

- AWS SAM
- AWS CodeBuild
- AWS CodeDeploy
- AWS CodePipeline

---

# AWS Serverless Application Model (AWS SAM)

AWS SAM is an **open-source framework** used to build and deploy serverless applications.

It simplifies Infrastructure as Code by using **YAML templates**.

During deployment:

```
AWS SAM Template
        │
        ▼
CloudFormation Template
        │
        ▼
AWS Resources
```

---

## Benefits of AWS SAM

- Less code
- Easy deployment
- Infrastructure as Code
- Built-in policy templates
- Works with CloudFormation

---

# AWS SAM CLI

AWS SAM CLI is a command-line tool for building, testing, debugging, and deploying serverless applications.

---

## Features

- Test Lambda locally
- Debug functions
- Generate test events
- Validate templates
- Deploy applications

---

## Common Commands

| Command | Purpose |
|----------|---------|
| `sam init` | Create a new SAM project |
| `sam build` | Build the application |
| `sam local` | Test locally |
| `sam validate` | Validate SAM template |
| `sam deploy` | Deploy application |

---

# Serverless CI/CD

AWS services used:

- AWS CodeBuild → Build & Test
- AWS CodeDeploy → Safe Deployments
- AWS CodePipeline → CI/CD Automation

---

# Key Takeaways

- Lambda supports multiple programming languages.
- The Handler is the entry point of a Lambda function.
- Event Object contains trigger information.
- Context Object contains runtime metadata.
- Keep Lambda functions modular and stateless.
- AWS SAM simplifies serverless deployments.
- AWS SAM CLI helps test and deploy applications locally.

---

# Configuring AWS Lambda Functions

When creating a Lambda function, three primary configuration settings determine its performance:

- Memory
- Timeout
- Concurrency

Proper configuration helps optimize **performance**, **scalability**, and **cost**.

---

# 1. Memory

Memory determines the amount of RAM allocated to a Lambda function.

## Key Points

- Configurable up to **10 GB**.
- CPU and other resources increase proportionally with memory.
- More memory can reduce execution time.

> More memory = More CPU = Faster execution

### Best Practice

- Test different memory configurations.
- Use **AWS Lambda Power Tuning** to find the optimal setting.

---

# 2. Timeout

Timeout specifies the maximum time a Lambda function can run.

## Key Points

- Maximum timeout: **900 seconds (15 minutes)**
- Lambda automatically terminates the function after the timeout.

### Best Practices

- Avoid setting the timeout to the maximum by default.
- Set the timeout slightly higher than the expected execution time.
- Use load testing to determine the optimal timeout.

---

# Lambda Billing

AWS Lambda follows a **pay-as-you-use** pricing model.

Billing depends on:

- Number of requests
- Execution duration
- Configured memory

> Billing is based on **configured memory**, not actual memory usage.

### Free Tier

- 1 Million requests/month
- 400,000 GB-seconds/month

---

# Lambda Power Tuning

AWS Lambda Power Tuning helps determine the best memory configuration.

### Optimization Strategies

- Cost
- Speed
- Balanced

Benefits:

- Lower execution time
- Lower cost
- Better performance

---

# Concurrency

Concurrency is the number of Lambda invocations running simultaneously.

Example:

If 5 requests arrive at the same time,

```
Concurrency = 5
```

---

# Types of Concurrency

## 1. Unreserved Concurrency

Default shared concurrency available for all Lambda functions.

---

## 2. Reserved Concurrency

Reserves a fixed number of concurrent executions for a specific function.

### Benefits

- Guarantees capacity
- Prevents other functions from consuming all concurrency

---

## 3. Provisioned Concurrency

Keeps execution environments warm.

### Benefits

- Eliminates cold starts
- Predictable low latency
- Ideal for real-time applications

---

# Concurrency Limits

Default Regional quota:

```
1000 Concurrent Executions
```

Can be increased by requesting a quota increase from AWS.

---

# Burst Scaling

Lambda automatically handles sudden traffic spikes.

Initial burst limits vary by Region.

Examples:

| Region | Initial Burst |
|----------|--------------|
| US East (N. Virginia) | 3000 |
| Europe (Ireland) | 3000 |
| Tokyo | 1000 |
| Frankfurt | 1000 |
| Other Regions | 500 |

After the initial burst, Lambda can scale by **1,000 additional concurrent executions every 10 seconds**.

---

# CloudWatch Metrics

Lambda automatically publishes metrics to Amazon CloudWatch.

Important metrics:

- ConcurrentExecutions
- UnreservedConcurrentExecutions

These metrics help monitor:

- Performance
- Scaling
- Throttling

---

# Testing Best Practices

- Test under real-world traffic.
- Simulate peak loads.
- Monitor CloudWatch metrics.
- Verify downstream services (RDS, DynamoDB, etc.).
- Test error handling.
- Measure throttling.

---

# Why Set Concurrency Limits?

Reasons include:

- Manage costs
- Protect downstream resources
- Reserve capacity for critical functions

---

# Deploying and Testing Serverless Applications

## Overview

Serverless deployment differs from traditional server-based deployment because developers deploy **both the application code and the required infrastructure**.

AWS uses **AWS CloudFormation** and **AWS Serverless Application Model (AWS SAM)** to automate deployment.

---

# Server-Based vs Serverless Deployment

| Server-Based Deployment | Serverless Deployment |
|-------------------------|-----------------------|
| Infrastructure already exists | Infrastructure is created during deployment |
| Developers deploy only application code | Developers deploy code and infrastructure together |
| DevOps manages servers | AWS manages infrastructure |
| Requires server management | No server management |

---

# Infrastructure as Code (IaC)

Infrastructure as Code (IaC) is the practice of managing infrastructure using code instead of manual configuration.

AWS uses **AWS CloudFormation** to provision infrastructure.

### Benefits

- Automated deployments
- Repeatable infrastructure
- Version-controlled templates
- Consistent environments

---

# AWS CloudFormation

AWS CloudFormation is an **Infrastructure as Code (IaC)** service that provisions AWS resources using templates.

### Features

- Creates AWS resources automatically
- Deploys resources as a **Stack**
- Uses JSON or YAML templates
- Ensures consistent deployments

### Stack

A **Stack** is a collection of AWS resources managed as a single unit.

---

# AWS Serverless Application Model (AWS SAM)

AWS SAM is an open-source framework that simplifies serverless application development.

AWS SAM transforms simplified templates into full CloudFormation templates.

```text
AWS SAM Template
        │
        ▼
CloudFormation Template
        │
        ▼
AWS Resources
```

### Benefits

- Less configuration
- Faster deployment
- Simplified Infrastructure as Code
- Easier serverless development

---

# Server-Based Development Workflow

1. Write Code
2. Test Locally
3. Commit Code
4. Build Application
5. Deploy to Development
6. Test
7. Deploy to Production

---

# Serverless Development Workflow

1. Write Code
2. Create AWS SAM Template
3. Deploy to AWS
4. Test in AWS Environment
5. Promote to Production

---

# Environment Parity

Environment parity means every environment uses the **same infrastructure configuration**.

AWS SAM ensures identical deployments across:

- Development
- Testing
- Staging
- Production

---

# Benefits of AWS SAM

- Consistent deployments
- Easy experimentation
- Faster deployments
- Infrastructure as Code
- Simplified CloudFormation templates

---

# Lambda Versioning

Every Lambda function has versions.

Initially, every function contains only:

```
$LATEST
```

Published versions are **immutable** (cannot be modified).

Example:

```
$LATEST
Version 1
Version 2
Version 3
```

---

# Lambda Aliases

Aliases provide friendly names for Lambda versions.

Example:

```
Development → Version 1

Testing → Version 2

Production → Version 5
```

Benefits:

- Easier deployments
- Traffic shifting
- Easy rollback

---

# Alias Routing

Alias routing allows traffic to be split between two Lambda versions.

Example:

```
Version 5 → 90%

Version 6 → 10%
```

Benefits

- Canary deployments
- Safe testing
- Reduced deployment risk

---

# AWS CodeDeploy

AWS CodeDeploy automates Lambda deployments.

It supports safe traffic shifting between Lambda versions.

### Deployment Strategies

## Canary Deployment

Traffic shifts in two stages.

Example:

```
10%
 ↓
90%
```

---

## Linear Deployment

Traffic shifts gradually over time.

Example:

```
10%
20%
30%
...
100%
```

---

## All-at-Once Deployment

All traffic immediately shifts to the new version.

```
Old Version
      │
      ▼
New Version (100%)
```

---

# Deployment Safety

AWS CodeDeploy supports:

### CloudWatch Alarms

Automatically rollback deployment when errors occur.

### Hooks

Run validation tests:

- Before deployment
- After deployment

---

# AutoPublishAlias

AWS SAM automatically:

- Publishes a new Lambda version
- Creates/updates an alias
- Routes traffic to the latest version

---

# Monitoring and Troubleshooting AWS Lambda

## Overview

AWS Lambda integrates with several AWS services to help monitor, debug, trace, and troubleshoot serverless applications.

Main monitoring services:

- Amazon CloudWatch
- Amazon CloudWatch Lambda Insights
- AWS X-Ray
- AWS CloudTrail
- Dead-Letter Queue (DLQ)

---

# Amazon CloudWatch

Amazon CloudWatch automatically collects metrics for Lambda functions.

It helps monitor:

- Performance
- Errors
- Resource usage
- Function health

---

## CloudWatch Metrics

### Invocations

Total number of times a Lambda function is executed.

---

### Duration

The time taken by a Lambda function to complete execution.

Measured in milliseconds.

---

### Errors

Number of function executions that failed.

---

### Throttles

Number of requests rejected because concurrency limits were reached.

---

### IteratorAge

Measures how long records remain unprocessed in stream-based services such as:

- Amazon Kinesis
- DynamoDB Streams

---

### DeadLetterErrors

Number of failures while sending failed events to the Dead-Letter Queue (DLQ).

---

### ConcurrentExecutions

The number of Lambda functions running simultaneously.

---

# Amazon CloudWatch Lambda Insights

Lambda Insights is an advanced monitoring and troubleshooting solution for AWS Lambda.

It collects:

- System-level metrics
- Performance metrics
- Diagnostic information

---

## Lambda Insights Provides

- Memory usage
- CPU utilization
- Network usage
- Cold starts
- Worker shutdowns
- Function cost
- Execution duration

---

## Dashboard Views

### Multi-Function View

Displays metrics for all Lambda functions within an AWS account and Region.

Useful for:

- Finding underutilized functions
- Finding overutilized functions

---

### Single-Function View

Displays detailed metrics for one Lambda function.

Useful for:

- Performance analysis
- Troubleshooting
- Debugging

---

# AWS X-Ray

AWS X-Ray helps analyze application performance and trace requests.

It records the complete execution path of a request.

---

## Uses of AWS X-Ray

- Trace requests
- Identify bottlenecks
- Debug errors
- Analyze performance
- Visualize service dependencies

---

## X-Ray Provides

- Service Map
- Trace Details
- Response Time
- Error Analysis

---

# Cold Start Analysis

X-Ray can identify delays caused by:

- Creating execution environments
- Initializing runtime
- Loading dependencies

Useful for optimizing Lambda performance.

---

# Warm Start Analysis

X-Ray shows faster execution because the execution environment is reused.

Benefits:

- Lower latency
- Faster response time

---

# AWS CloudTrail

AWS CloudTrail records API activity performed within an AWS account.

It is mainly used for:

- Auditing
- Security
- Compliance
- Investigating account activity

Example:

- Who deleted a Lambda function?
- Who modified IAM permissions?

---

# Dead-Letter Queue (DLQ)

A Dead-Letter Queue stores events that Lambda cannot process successfully.

Supported Services:

- Amazon SQS
- Amazon SNS

---

## Benefits

- Prevents event loss
- Enables manual investigation
- Supports retry mechanisms

---

# Monitoring Tool Comparison

| Tool | Purpose |
|------|---------|
| Amazon CloudWatch | Monitor metrics, errors, duration, throttling |
| Lambda Insights | Detailed performance monitoring |
| AWS X-Ray | Request tracing and bottleneck analysis |
| AWS CloudTrail | Audit AWS API activity |
| Dead-Letter Queue | Store failed events |

---

