# AWS Lambda — Serverless Compute (Exam Notes)

## What Is AWS Lambda? (EXAM CRITICAL)
**AWS Lambda** is a **serverless compute service** that lets you:
- Upload code as a **Lambda function**
- Run code **only in response to events**
- Avoid managing servers or infrastructure

➡️ Lambda functions are **not always running**.

---

## How AWS Lambda Works
1. You upload your code (Lambda function)
2. You configure one or more **triggers**
3. AWS waits for an event
4. When triggered:
   - Code runs automatically
   - In a managed, scalable environment

---

## Common Lambda Triggers (EXAM FAVORITES)
- HTTP requests (API Gateway, ALB)
- Amazon S3 events (object upload)
- Other AWS services
- Application or mobile app events

---

## What AWS Manages vs What You Manage

### AWS Manages
- Server provisioning
- Scaling
- High availability
- OS maintenance
- Patching

---

### You Manage
- Function code
- Runtime (language)
- Memory & CPU allocation
- Permissions (IAM role)
- Dependencies
- Triggers

---

## Lambda Runtime & Limits (EXAM CRITICAL)
- Supported runtimes:
  - Python
  - Node.js
  - Java
  - Go
  - .NET
  - (and others)
- **Maximum execution time: 15 minutes**
- Each invocation runs in:
  - Its own isolated environment

⚠️ Lambda is **NOT** for:
- Long-running jobs
- Batch processing
- Hosting websites (e.g., WordPress)

---

## Lambda Scaling Behavior (EXAM FAVORITE)
- Automatically scales with demand
- Handles:
  - 1 request
  - 1,000+ requests
- Each trigger = separate execution environment

---

## Lambda Pricing Model (VERY IMPORTANT)
- You are billed:
  - **Only when code runs**
  - Per millisecond of execution
- No charge when idle
- Pay for:
  - Execution duration
  - Allocated memory

➡️ Very cost-effective for event-driven workloads

---

## IAM & Lambda Security (EXAM TRAP)
- Lambda uses **IAM roles**, not users
- Permissions are delegated via:
  - **Execution role**
- Example:
  - Lambda role allowing read/write access to S3

---

## Lambda + S3 Example Pattern (EXAM SCENARIO)
- Event:
  - File uploaded to S3
- Trigger:
  - S3 PUT operation
- Action:
  - Lambda processes file (e.g., image resize)
  - Output saved to a different S3 prefix

### Best Practice
- Use **input/output prefixes**
- Avoid recursive Lambda invocations

---

## Lambda Supports Containers (EXAM DETAIL)
- Lambda can run:
  - ZIP packages
  - Container images
- Useful when:
  - You need custom dependencies

---

## When to Use AWS Lambda (EXAM DECISION)
Use Lambda when:
- Workloads are event-driven
- Execution is short-lived
- You want zero server management
- You want automatic scaling

---

## When NOT to Use AWS Lambda
- Long-running processes
- High-performance computing
- Stateful applications
- Always-on servers

---

## Exam Takeaway Summary
- Lambda = serverless, event-driven compute
- Runs only when triggered
- Max runtime = **15 minutes**
- Scales automatically
- Pay per millisecond
- Uses IAM roles for permissions
