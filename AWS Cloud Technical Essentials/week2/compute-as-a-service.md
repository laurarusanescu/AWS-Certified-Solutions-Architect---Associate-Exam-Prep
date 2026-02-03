# Compute as a Service on AWS — Exam Notes

## What Is a Server?
- A **server** is a computer (or group of computers) that:
  - Receives requests from clients
  - Processes those requests
  - Returns responses
- Common model:
  - **Client–Server Model**
    - Client = user or device sending a request
    - Server = system handling the request

---

## Servers and Web Applications
- Servers commonly handle:
  - **HTTP requests**
  - API-based communication
- Servers provide:
  - CPU
  - Memory
  - Networking
- Used to process user requests and generate responses

---

## Common HTTP Server Software
- **Windows-based**:
  - Internet Information Services (IIS)
- **Linux-based**:
  - Apache HTTP Server
  - Nginx
  - Apache Tomcat

---

## Compute on AWS
- To run servers on AWS, you use **compute services**
- AWS provides compute options via the **AWS Management Console**

---

## Types of Compute Options on AWS (EXAM CRITICAL)
At a high level, AWS offers **three compute models**:

1. **Virtual Machines**
2. **Container Services**
3. **Serverless Compute**

---

## Virtual Machines (FOUNDATIONAL CONCEPT)
- Virtual machines emulate **physical servers**
- Allow you to:
  - Install an operating system
  - Install an HTTP server
  - Run applications
- Familiar to users with on-premises experience

---

## Amazon EC2 — EXAM CORE SERVICE
- **Amazon Elastic Compute Cloud (EC2)** provides:
  - Virtual machines in AWS
- EC2 uses **virtualization** under the hood

### How EC2 Works (High Level)
- AWS manages:
  - Physical host machines
  - Hypervisor layer
- EC2 instances run:
  - A **guest operating system**
  - User-installed software and applications

---

## Hypervisor Concept (EXAM KNOWLEDGE)
- A **hypervisor**:
  - Runs on physical hardware
  - Allocates CPU, memory, and networking
  - Creates and manages virtual machines
- In AWS:
  - Hypervisor is fully managed by AWS
  - Customers never interact with it directly

---

## Why EC2 Is Important
- Many AWS compute services:
  - Are built on EC2
  - Use virtualization concepts
- Understanding EC2 makes it easier to learn:
  - Container services
  - Serverless services

---

## Exam Takeaway Summary
- Compute = servers that process requests
- EC2 = virtual machines in AWS
- AWS manages:
  - Hardware
  - Hypervisor
- You manage:
  - OS configuration
  - Applications
- EC2 knowledge is **foundational for all compute questions**
