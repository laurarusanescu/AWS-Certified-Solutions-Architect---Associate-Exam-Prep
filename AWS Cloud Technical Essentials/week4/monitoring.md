# Monitoring & Amazon CloudWatch — Exam Notes

---

## What Is Monitoring? (EXAM CRITICAL)
**Monitoring** is the process of:
- Collecting
- Analyzing
- Using data

to understand the **operational health, performance, and usage** of AWS resources.

➡️ Monitoring gives you **near real-time visibility** into your systems.

---

## Why Monitoring Matters
Monitoring helps answer questions like:
- How many users are visiting my site?
- Is my application performing well?
- Are resources running out of capacity?
- Will I be alerted if something fails?

---

## Metrics (EXAM CRITICAL)

### What Is a Metric?
- A **metric** is a single data point produced by a resource
- Metrics collected over time form **statistics**
  - Example: average CPU utilization

---

### Common EC2 Metrics
- CPU utilization
- Network utilization
- Disk performance
- Memory utilization (via custom metrics)
- Application logs

---

### Metrics Differ by Service (EXAM FAVORITE)

#### Amazon EC2
- CPU utilization
- Network traffic
- Disk I/O

#### Amazon S3
- Bucket size
- Number of objects
- Read/write requests

#### Amazon RDS
- Database connections
- CPU utilization
- Disk space usage

➡️ Different services emit **different metrics**

---

## Using Metrics to Detect Problems
- High CPU for extended time may indicate:
  - Traffic spikes
  - Application bugs
- Metrics can trigger:
  - Alerts
  - Manual actions
  - Automated actions (e.g., scaling)

---

## Benefits of Monitoring (EXAM FAVORITE)

### 1. Proactive Issue Detection
- Identify problems **before users notice**
- Monitor:
  - Error rates
  - Latency
  - Resource exhaustion

---

### 2. Improve Performance & Reliability
- Identify bottlenecks
- Detect inefficient architectures
- Improve system design

---

### 3. Detect Security Threats
- Establish a **baseline** of normal behavior
- Identify anomalies:
  - Traffic spikes
  - Unusual IP addresses
- Trigger alerts or investigations

---

### 4. Make Data-Driven Business Decisions
- Track feature usage
- Measure user engagement
- Decide where to invest development effort

---

### 5. Optimize Costs
- Identify underutilized resources
- Right-size infrastructure
- Reduce unnecessary spending

---

## Amazon CloudWatch (EXAM CRITICAL)

### What Is Amazon CloudWatch?
**Amazon CloudWatch** is AWS’s **monitoring and observability service**.

It provides:
- Centralized visibility
- Metrics
- Logs
- Events
- Alarms

➡️ Unified view of operational health

---

## What CloudWatch Collects
- Metrics
- Logs
- Events
- Network traffic data

---

## What You Can Do with CloudWatch (MEMORIZE)
- Detect anomalous behavior
- Set **alarms**
- Visualize metrics and logs
- Trigger automated actions (e.g., Auto Scaling)
- Troubleshoot issues
- Gain operational insights

---

## CloudWatch Alarms (EXAM FAVORITE)
- Alarms watch **metrics**
- Trigger actions when thresholds are crossed
- Actions can include:
  - Notifications
  - Auto Scaling
  - Automated recovery

---

## Exam Takeaway Summary
- Monitoring = visibility into system health
- Metrics = data points over time
- Different AWS services emit different metrics
- CloudWatch centralizes monitoring
- Alarms enable proactive responses
- Monitoring improves reliability, security, and cost efficiency
