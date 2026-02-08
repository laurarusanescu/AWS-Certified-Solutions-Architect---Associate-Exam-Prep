# Optimizing Solutions on AWS — Availability & High Availability (Exam Notes)

---

## What Is Availability? (EXAM CRITICAL)
**Availability** measures how long a system is operational over a given time period.

- Expressed as:
  - Percentage of uptime
  - Number of “nines”

---

## Availability vs Downtime (MEMORIZE)

| Availability | Downtime per Year |
|-------------|------------------|
| 90% (1 nine) | 36.53 days |
| 99% (2 nines) | 3.65 days |
| 99.9% (3 nines) | 8.77 hours |
| 99.95% (3.5 nines) | 4.38 hours |
| 99.99% (4 nines) | 52.6 minutes |
| 99.995% (4.5 nines) | 26.3 minutes |
| 99.999% (5 nines) | 5.26 minutes |

➡️ Higher availability = **less downtime**

---

## Redundancy Increases Availability (EXAM GOLD)
- Availability is improved through **redundancy**
- Redundancy means:
  - More servers
  - More databases
  - More data replication
  - More Availability Zones

⚠️ More redundancy = **higher cost**

➡️ Architects must balance:
- Availability
- Cost
- Business value

---

## Single Point of Failure (EXAM FAVORITE)
- A system with **one EC2 instance** has a **single point of failure**
- Even if:
  - S3 is highly available
  - DynamoDB is highly available
- If the EC2 instance fails → app is down

---

## Improve Availability with Multiple Instances

### Step 1: Add Another Instance
- Deploy **more than one EC2 instance**
- Removes single point of failure

---

### Step 2: Use Multiple Availability Zones (EXAM CRITICAL)
- Place instances in **different AZs**
- Protects against:
  - OS failures
  - Application failures
  - Hardware failures
  - AZ-level failures

---

## New Challenges with Multiple Instances

### 1. Replication
- Need to replicate:
  - Application code
  - Configuration
  - Patches
- Best practice:
  - **Automate** deployments

---

### 2. Client Redirection (EXAM FAVORITE)

#### DNS-Based Redirection
- One DNS record points to multiple IPs
- Downside:
  - DNS propagation delay

---

#### Load Balancer (BEST PRACTICE)
- Distributes traffic automatically
- Performs health checks
- No propagation delay
- Sits between:
  - Client
  - Servers

➡️ **Preferred solution in AWS**

---

## Types of High Availability Architectures

### Active–Passive (EXAM DETAIL)
- Only **one instance serves traffic**
- Second instance is standby
- Advantages:
  - Works well for **stateful apps**
- Disadvantages:
  - No load sharing
  - Limited scalability

---

### Active–Active (EXAM GOLD)
- **All instances serve traffic**
- Advantages:
  - High availability
  - Better scalability
- Works best for:
  - **Stateless applications**
- Disadvantage:
  - Stateful apps require session sharing

---

## Stateful vs Stateless (EXAM TRAP)
- **Stateful apps**:
  - Store session data on server
  - Harder to scale horizontally
- **Stateless apps**:
  - No session data stored on server
  - Ideal for active–active architectures

---

## Exam Takeaway Summary
- Availability measured in “nines”
- Redundancy improves availability
- Single EC2 = single point of failure
- Multi-AZ deployments are critical
- Load balancers solve redirection issues
- Active–active = scalable & preferred
- Stateless apps scale best
