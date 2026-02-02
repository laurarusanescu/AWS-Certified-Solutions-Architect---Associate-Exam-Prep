# AWS Cloud Foundations — Exam-Focused Notes (Solutions Architect Associate)

## Cloud Computing Fundamentals
- **Cloud computing**: On-demand delivery of IT resources over the internet with pay-as-you-go pricing
- **Key benefits**:
  - Cost optimization (no upfront hardware)
  - Scalability and elasticity
  - High availability and fault tolerance
  - Faster innovation and deployment
- **When to use cloud**:
  - Variable or unpredictable workloads
  - Need for rapid scaling
  - Global applications

---

## AWS Global Infrastructure
- **Region**:
  - A geographical area (e.g., eu-west-1)
  - Consists of multiple Availability Zones
- **Availability Zone (AZ)**:
  - One or more physically separate data centers
  - Designed for **fault isolation**
- **Best practice**:
  - Deploy applications across **multiple AZs** for high availability

---

## Interacting with AWS
- **AWS Management Console** (web UI)
- **AWS CLI**
- **AWS SDKs**
- Understanding AWS terminology is critical for:
  - Reading AWS documentation
  - Designing architectures
  - Exam questions

---

## Core Networking Concept
### Amazon VPC (Virtual Private Cloud)
- A **logically isolated private network** in AWS
- Used to host application resources securely
- Key exam idea:
  - Most workloads run **inside a VPC**

---

## Core Compute
### Amazon EC2 (Elastic Compute Cloud)
- Provides **virtual machines** in AWS
- Used to run backend applications
- Key exam idea:
  - EC2 = Infrastructure as a Service (IaaS)

---

## Storage Services
### Amazon S3 (Simple Storage Service)
- **Object storage**
- Stores files like images, videos, backups
- Key characteristics:
  - Virtually unlimited storage
  - Highly durable
- Common exam use cases:
  - Static assets
  - Media storage

### Amazon RDS (Relational Database Service)
- Managed **relational database**
- Runs inside a VPC
- Key exam idea:
  - AWS manages backups, patching, and availability

---

## High Availability & Scalability
### Elastic Load Balancing (ELB)
- Distributes incoming traffic across multiple targets
- Improves availability and fault tolerance

### EC2 Auto Scaling
- Automatically adds or removes EC2 instances
- Ensures:
  - Scalability
  - Cost efficiency
  - High availability

---

## Monitoring
### Amazon CloudWatch
- Monitoring and observability service
- Tracks:
  - Metrics
  - Logs
  - Alarms
- Used to monitor application health and performance

---

## Security & Identity
### AWS Identity and Access Management (IAM)
- Controls **who** can access **what** in AWS
- Core components:
  - Users
  - Roles
  - Policies
- **Exam-critical principle**:
  - **Least privilege**
- Important:
  - Secure the AWS account immediately after creation

---

## Typical Exam Architecture Pattern
- Application runs in a **VPC**
- Backend on **EC2**
- Database on **RDS**
- Static assets on **S3**
- Traffic managed by **ELB**
- Scaling with **Auto Scaling**
- Monitoring via **CloudWatch**
- Access control via **IAM**

---
