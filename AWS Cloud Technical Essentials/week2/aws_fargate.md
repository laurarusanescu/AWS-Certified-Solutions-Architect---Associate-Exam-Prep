# AWS Fargate — Serverless Containers (Exam Notes)

## Container Architecture Recap
A container-based architecture has **two main parts**:

1. **Container Orchestrator**
   - Manages container lifecycle
   - Examples:
     - Amazon ECS
     - Amazon EKS

2. **Compute Platform**
   - Where containers actually run
   - Options:
     - Amazon EC2 (traditional)
     - AWS Fargate (serverless)

---

## EC2 vs Fargate for Containers (EXAM CRITICAL)

### Containers on EC2
- You manage:
  - EC2 instances
  - Operating system
  - Patching
  - Scaling infrastructure
- More control
- More operational overhead

---

### AWS Fargate — Serverless Compute for Containers
- **AWS Fargate** is a **serverless compute platform** for containers
- Works with:
  - Amazon ECS
  - Amazon EKS

➡️ You **do not manage servers or instances**

---

## What AWS Fargate Manages
With Fargate, AWS handles:
- Server provisioning
- OS management
- Patching
- Cluster capacity
- Infrastructure scaling
- Fault tolerance

➡️ Scaling and high availability are **built in**

---

## What YOU Define with Fargate
You define:
- Container images
- CPU and memory requirements
- Networking
- Storage
- Scaling requirements

---

## How Fargate Works (High Level)
1. Build container images
2. Push images to a repository
   - Example: **Amazon ECR (Elastic Container Registry)**
3. Define:
   - ECS **Task** (ECS)
   - Kubernetes **Pod** (EKS)
4. Run containers on Fargate
5. Pay only for resources used

---

## Fargate Pricing Model (EXAM RELEVANT)
- Pay for:
  - vCPU
  - Memory
  - Storage
- Billed based on **actual usage**
- Supports:
  - Spot pricing
  - Compute Savings Plans

---

## ECS / EKS + Fargate Mapping (EXAM TRAP)

| Orchestrator | Compute | Unit |
|-------------|--------|------|
| ECS | EC2 | Task |
| ECS | Fargate | Task |
| EKS | EC2 | Pod |
| EKS | Fargate | Pod |

---

## Use Cases for AWS Fargate
- Microservices architectures
- Batch processing
- Machine learning workloads
- Migrating on-premises containerized apps
- Event-driven container workloads

---

## When to Choose Fargate (EXAM DECISION)
Choose **AWS Fargate** when:
- You want **serverless containers**
- You don’t want to manage EC2 instances
- You want built-in scaling and fault tolerance
- You prefer operational simplicity

---

## When NOT to Choose Fargate
- You need:
  - Full control over OS
  - Custom instance-level configuration
- You already manage complex EC2-based clusters

---

## Exam Takeaway Summary
- ECS/EKS = orchestration
- EC2 = you manage servers
- Fargate = serverless compute for containers
- No provisioning, patching, or scaling infra
- Pay only for vCPU and memory used
