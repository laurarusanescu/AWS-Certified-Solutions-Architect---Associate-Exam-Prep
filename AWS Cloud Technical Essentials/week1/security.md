# Security and the AWS Shared Responsibility Model — Exam Notes

## Shared Responsibility Model (EXAM CRITICAL)
Security and compliance in AWS are a **shared responsibility** between:
- **AWS** → *Security **of** the cloud*
- **Customer** → *Security **in** the cloud*

---

## Security **OF** the Cloud (AWS Responsibility)
AWS is responsible for protecting the **underlying infrastructure** that runs AWS services.

### AWS is responsible for:
- Physical security of:
  - Data centers
  - Buildings
  - Regions and Availability Zones
- Managing:
  - Physical servers
  - Host operating systems
  - Virtualization layer
  - AWS networking components

➡️ Customers **do not** manage or access AWS physical infrastructure.

---

## AWS Responsibility by Service Category

### 1. Infrastructure Services (Least Abstracted)
**Example**:
- Amazon EC2

**AWS manages**:
- Physical data centers
- Hardware
- Networking
- Virtualization layer

---

### 2. Container Services (Medium Abstraction)
**Examples**:
- Amazon RDS

**AWS manages**:
- Infrastructure
- Operating system
- Application platform

> Note: “Container services” here means AWS abstracts the platform — **not Docker containers**.

---

### 3. Abstracted Services (Most Abstracted)
**Examples**:
- Amazon S3

**AWS manages**:
- Infrastructure
- Operating system
- Platform
- Server-side encryption
- Data durability and protection

---

## Security **IN** the Cloud (Customer Responsibility)
You are responsible for:
- **Configuring AWS services securely**
- **Protecting your data**
- **Managing access and permissions**

➡️ Your responsibility **increases** as the service becomes **less abstracted**.

---

## Customer Responsibility by Service Category

### Infrastructure Services (EC2)
You are responsible for:
- Operating system configuration
- OS patching
- Application security
- Data encryption
- Data protection

---

### Container Services (RDS)
You are responsible for:
- Customer data
- Encrypting data
- Network security (firewalls, security groups)
- Backups

---

### Abstracted Services (S3)
You are responsible for:
- Customer data
- Access control (IAM, bucket policies)
- Client-side encryption (if required)

---

## Key Exam Rule (VERY IMPORTANT)
👉 **You always own and control your data**, regardless of the service.

---

## Examples of Customer Responsibilities (EXAM FAVORITES)
- Choosing AWS Regions based on:
  - Data sovereignty
  - Compliance requirements
- Implementing data protection:
  - Encryption
  - Backups
- Managing access:
  - IAM users
  - Roles
  - Policies
  - Least privilege principle

---

## High-Level Exam Summary
- AWS secures the **cloud infrastructure**
- You secure:
  - Your data
  - Your configurations
  - Your access controls
- More abstraction = less customer responsibility
- Less abstraction = more customer responsibility
