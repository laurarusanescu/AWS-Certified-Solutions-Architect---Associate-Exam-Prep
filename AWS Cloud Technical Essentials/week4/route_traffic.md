# Route Traffic with Amazon Elastic Load Balancing (ELB) — Exam Notes

---

## What Is a Load Balancer? (EXAM CRITICAL)
A **load balancer** distributes incoming traffic across multiple backend resources.

- Tasks = incoming requests
- Resources = EC2 instances, containers, IPs, or Lambda

➡️ Eliminates single points of failure  
➡️ Improves **availability and scalability**

---

## Elastic Load Balancing (ELB)
**ELB** is a fully managed AWS service that:
- Distributes traffic automatically
- Requires no infrastructure management
- Scales automatically
- Is highly available by default

---

## ELB Capabilities (EXAM FAVORITE)
ELB can route traffic to:
- EC2 instances
- Containers (ECS / EKS)
- IP addresses
- AWS Lambda functions

➡️ Supports **hybrid architectures** (on-prem + AWS)

---

## High Availability with ELB
- ELB must be deployed across:
  - **Multiple Availability Zones**
- AWS manages:
  - Scaling
  - Fault tolerance
- You ensure:
  - Multi-AZ configuration

---

## Health Checks (EXAM CRITICAL)

### Why Health Checks Matter
- Port open ≠ application healthy
- Health checks determine:
  - Whether traffic is sent to a target

---

### Best Practice Health Checks
- Validate:
  - Application logic
  - Database connectivity
  - S3 access
- Example endpoint:
  - `/monitor`

➡️ ELB routes traffic **only to healthy targets**

---

## ELB + Auto Scaling Integration
- If an instance becomes unhealthy:
  - ELB stops sending traffic
  - Auto Scaling replaces it
- During scale-down:
  - ELB waits for active connections to finish
  - Prevents new connections

➡️ This feature is called **connection draining**
(also known as *deregistration delay*)

---

## Core ELB Components (EXAM FAVORITE)

### Listeners
- Client-side entry point
- Define:
  - Port
  - Protocol
- A load balancer can have:
  - Multiple listeners

---

### Target Groups
- Backend resources
- Define:
  - Target type (EC2, IP, Lambda)
  - Health checks

---

### Rules
- Connect listeners to target groups
- Based on conditions such as:
  - Path
  - Host
  - Source IP
  - Headers

---

## Application Load Balancer (ALB) (EXAM GOLD)

### Key Characteristics
- Layer 7 (HTTP/HTTPS)
- Understands request content

---

### Routing Capabilities
- Route based on:
  - URL path (`/upload`)
  - Host name
  - HTTP headers
  - HTTP method
  - Source IP

---

### Additional Features
- Redirects (HTTP → HTTPS)
- Fixed responses (custom HTML)
- User authentication
- Sticky sessions (cookies)
- TLS termination (HTTPS offloading)

---

### Security
- Uses **security groups**
- SSL certificates via:
  - AWS Certificate Manager (ACM)
  - IAM

---

### Routing Algorithms
- **Round-robin**
- **Least outstanding requests**
  - Best when:
    - Requests vary in complexity
    - Instances differ in size

---

### When to Use ALB
- Web applications
- Microservices
- REST APIs
- HTTP/HTTPS traffic

---

## Network Load Balancer (NLB) (EXAM CRITICAL)

### Key Characteristics
- Layer 4 (connection level)
- Supports:
  - TCP
  - UDP
  - TLS

---

### Routing Behavior
- Uses **flow hash** based on:
  - Source/destination IP
  - Ports
  - Protocol
  - TCP sequence

---

### Features
- Preserves **source IP address**
- Supports **static & Elastic IPs**
- Handles **millions of requests per second**
- Sticky sessions based on **source IP**
- TLS termination supported

---

### When to Use NLB
- Non-HTTP protocols
- Extreme performance requirements
- Need for static IP addresses
- Applications requiring client IP visibility

---

## ALB vs NLB (EXAM COMPARISON)

| Feature | ALB | NLB |
|------|----|----|
| OSI Layer | Layer 7 | Layer 4 |
| Protocols | HTTP, HTTPS | TCP, UDP, TLS |
| Content-based routing | ✔ | ❌ |
| User authentication | ✔ | ❌ |
| Sticky sessions | Cookie-based | Source IP |
| TLS termination | ✔ | ✔ |
| Static IP support | ❌ | ✔ |
| Preserve source IP | ❌ | ✔ |

---

## Exam Takeaway Summary
- ELB distributes traffic & improves availability
- Always use **Multi-AZ**
- Health checks are critical
- ALB = smart HTTP routing
- NLB = high-performance, low-level routing
- Choose load balancer based on **protocol & features**
