# Amazon EC2 Auto Scaling — Exam Notes

---

## Why Auto Scaling Is Needed (EXAM CRITICAL)
- Adding more servers improves availability
- But **capacity issues** can still cause outages
- Auto Scaling solves:
  - Traffic spikes
  - Underutilization
  - Instance failures

---

## Vertical Scaling vs Horizontal Scaling (EXAM FAVORITE)

### Vertical Scaling (Scale Up / Down)
- Increase instance size or type
- Requires:
  - Stopping the instance
- Has limits:
  - Max instance size
- Common in:
  - **Active–Passive architectures**

⚠️ Manual, limited, and not elastic

---

### Horizontal Scaling (Scale Out / In)
- Add or remove instances
- No application changes if:
  - App is **stateless**
- Common in:
  - **Active–Active architectures**

➡️ Preferred cloud-native approach

---

## Stateless Applications (EXAM GOLD)
- Do not store session data on the server
- Enable:
  - Horizontal scaling
  - Load balancing
  - Auto Scaling
- Required for:
  - Active–active systems

---

## What Is Amazon EC2 Auto Scaling? (EXAM CRITICAL)
**EC2 Auto Scaling** automatically:
- Adds EC2 instances when demand increases
- Removes EC2 instances when demand decreases
- Replaces unhealthy instances

➡️ Ensures **availability + cost efficiency**

---

## ELB + EC2 Auto Scaling Integration (EXAM FAVORITE)
- New instances:
  - Registered with ELB
  - Receive traffic **only after passing health checks**
- Unhealthy instances:
  - Removed from ELB
  - Replaced automatically
- Scale-in events:
  - ELB drains connections
  - Prevents new connections

---

## EC2 Auto Scaling Core Components (MEMORIZE)

### 1. Launch Template
Defines **what** to launch:
- AMI
- Instance type
- Security groups
- EBS volumes
- Tags

#### Launch Template Benefits
- Supports versioning
- Can be created from:
  - Existing EC2 instance
  - Existing template
  - From scratch

➡️ **Preferred over launch configurations**

---

### 2. Auto Scaling Group (ASG)
Defines **where** to launch instances:
- VPC
- Subnets (must span **multiple AZs**)

---

### ASG Capacity Settings (EXAM CRITICAL)
- **Minimum**: lowest number of instances
- **Maximum**: highest allowed number
- **Desired**: target number of instances

➡️ Auto Scaling adjusts to match desired capacity

---

### ASG Availability Pattern
- Set min = max = desired
- Auto Scaling replaces failed instances
- Used for:
  - **Fleet management**
  - High availability without scaling

---

### Instance Purchasing Options
- On-Demand
- Spot
- Mixed (recommended for cost optimization)

---

### 3. Scaling Policies
Define **when** to scale.

Scaling decisions are based on:
- CloudWatch metrics
- CloudWatch alarms

---

## Scaling Policy Types (EXAM CRITICAL)

### Simple Scaling
- Triggered by a CloudWatch alarm
- Adds/removes:
  - Fixed number
  - Percentage of ASG
- Uses **cooldown period**

⚠️ Cannot respond to escalating demand quickly

---

### Step Scaling
- Responds to multiple thresholds
- Example:
  - CPU ≥ 70% → +1 instance
  - CPU ≥ 85% → +2 instances
  - CPU ≥ 95% → +4 instances

➡️ More responsive than simple scaling

---

### Target Tracking (EXAM GOLD)
- Track a target value (e.g., CPU = 60%)
- AWS manages alarms automatically
- Works well for:
  - CPU utilization
  - Network utilization
  - Request count

➡️ **Recommended scaling policy**

---

## Traditional Scaling vs Auto Scaling (EXAM FAVORITE)

### Traditional Scaling
- Provision for peak traffic
- Results in:
  - Idle resources
  - Wasted cost

---

### Auto Scaling
- Matches capacity to demand
- Scales automatically
- Pay only for what you use

---

## Exam Takeaway Summary
- Vertical scaling = manual, limited
- Horizontal scaling = elastic, preferred
- Stateless apps scale best
- Auto Scaling improves availability & cost
- Launch templates define instances
- ASGs define placement & capacity
- Target tracking is the best default policy
