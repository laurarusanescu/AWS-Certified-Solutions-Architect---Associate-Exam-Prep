# Container Services on AWS — Exam Notes

## AWS Compute Options (RECAP)
AWS offers three main compute models:
1. Virtual Machines (EC2)
2. Containers
3. Serverless

➡️ No one-size-fits-all — choose based on workload needs.

---

## What Is a Container? (EXAM CRITICAL)
- A **container** is a standardized unit that packages:
  - Application code
  - Dependencies
- Runs in an **isolated environment**
- Designed to run **consistently across environments**
  - Dev → Test → Prod
  - On-prem → Cloud

### Key Benefit
- Solves the “it works on my machine” problem

---

## Docker
- **Docker** is a popular container runtime
- Simplifies:
  - Creating
  - Packaging
  - Deploying
  - Running containers
- Manages OS-level isolation, networking, and storage

---

## Containers vs Virtual Machines (VERY IMPORTANT)

### Containers
- Share the **host OS and kernel**
- Lightweight
- Start **almost instantly**
- Ideal for:
  - Rapid scaling
  - Microservices

### Virtual Machines
- Each VM has its **own OS**
- Heavier
- Slower startup
- More isolation and OS-level control

➡️ Containers = speed & efficiency  
➡️ VMs = flexibility & full OS control

---

## Why You Need Container Orchestration
In real systems:
- Many containers
- Many EC2 instances
- Multiple Availability Zones

You must manage:
- Container placement
- Container failures
- Instance failures
- Scaling
- Monitoring

➡️ This is handled by **container orchestration services**

---

## AWS Container Orchestration Services
AWS provides two main services:
- **Amazon ECS**
- **Amazon EKS**

---

## Amazon Elastic Container Service (ECS)

### What Is ECS?
- AWS-native container orchestration service
- Runs containers on:
  - EC2
  - (or AWS Fargate — serverless containers)

---

### ECS Core Concepts (EXAM FAVORITES)
- **Container Instance**:
  - EC2 instance with **ECS Agent** installed
- **Task**:
  - A running container
- **Task Definition**:
  - JSON blueprint describing:
    - CPU
    - Memory
    - Container image
    - Ports
    - Networking

---

### ECS Capabilities
- Launch and stop containers
- Scale in and out
- Schedule containers across instances
- Meet availability requirements
- Assign permissions

---

## Amazon Elastic Kubernetes Service (EKS)

### What Is Kubernetes?
- Open-source container orchestration platform
- Industry standard
- Portable across environments

---

### What Is EKS?
- Managed Kubernetes service on AWS
- Used when:
  - You already use Kubernetes
  - You want fine-grained control
  - You want Kubernetes portability

---

### ECS vs EKS Terminology (EXAM TRAP)

| Concept | ECS | EKS |
|------|----|----|
| Host | Container Instance | Worker Node |
| Running unit | Task | Pod |
| Technology | AWS-native | Kubernetes |

---

## When to Use ECS vs EKS (EXAM DECISION)

### Use ECS When:
- You want simplicity
- You want AWS-native integration
- You don’t need Kubernetes features

### Use EKS When:
- You already use Kubernetes
- You want portability
- You need advanced orchestration control

---

## Exam Takeaway Summary
- Containers = lightweight, fast, portable
- Docker = container runtime
- Containers share OS; VMs do not
- ECS = AWS-native orchestration
- EKS = Kubernetes on AWS
- Task ≠ Pod
- Container Instance ≠ Worker Node
