# Introduction to Amazon CloudWatch — Exam Notes

---

## How CloudWatch Works (EXAM CRITICAL)
- CloudWatch is a **managed service**
- Requires only an AWS account
- No infrastructure to manage

➡️ Centralized place to collect and analyze metrics from **multiple AWS services**

---

## Basic vs Detailed Monitoring (EXAM FAVORITE)

### Basic Monitoring
- Enabled by default
- Metrics sent:
  - Every **5 minutes**
- Free
- Sufficient for many workloads

---

### Detailed Monitoring
- Metrics sent:
  - Every **1 minute**
- Additional cost
- Useful for:
  - Faster detection
  - High-sensitivity workloads

---

## CloudWatch Metrics Structure

### Namespaces (EXAM DETAIL)
- Metrics are grouped into **namespaces**
- Each AWS service has its own namespace
- Metrics in different namespaces are isolated

---

### Dimensions (EXAM CRITICAL)
- **Name/value pairs** that identify a metric
- Used to filter metrics
- Example:
  - `InstanceId = i-123456789`

➡️ Same metric can be viewed per resource using dimensions

---

## Custom Metrics (EXAM FAVORITE)

### What Are Custom Metrics?
- Application-level metrics
- Published by **you**
- Used when default AWS metrics are not enough

---

### Examples of Custom Metrics
- Page views
- Request error rates
- Page load times
- Application throughput
- Thread/process counts

---

### High-Resolution Custom Metrics
- Resolution up to **1 second**
- Used for:
  - Near real-time monitoring
- Published using:
  - `PutMetricData` API

---

## CloudWatch Dashboards (EXAM CRITICAL)

### What Is a Dashboard?
- Customizable visualization
- Displays:
  - Metrics
  - Logs
- Built using **widgets** (graphs, text)

---

### Dashboard Capabilities
- Multiple dashboards per account
- Combine metrics from:
  - Multiple services
  - Multiple Regions
- Display:
  - Aggregated data
  - Live data (last 1 minute)

---

### Dashboard Security
- Controlled using:
  - IAM users
  - IAM groups
  - IAM roles

---

## CloudWatch Logs (EXAM CRITICAL)

### What Are CloudWatch Logs?
- Centralized log storage and analysis
- Supports logs from:
  - EC2
  - AWS Lambda
  - Other AWS services

---

### Sending Logs to CloudWatch
- **AWS Lambda**
  - Minimal configuration
  - Requires IAM permissions
- **EC2**
  - Requires CloudWatch Logs agent

---

### CloudWatch Logs Agent (EXAM DETAIL)
Includes:
- CLI plugin
- Initialization script
- Daemon + cron job

➡️ Automatically pushes logs to CloudWatch

---

## CloudWatch Logs Terminology (MEMORIZE)

### Log Event
- Single log entry
- Has:
  - Timestamp
  - Message

---

### Log Stream
- Sequence of log events
- Typically from:
  - One EC2 instance
  - One Lambda function

---

### Log Group
- Collection of log streams
- Shared:
  - Retention settings
  - Permissions

---

## CloudWatch Alarms (EXAM CRITICAL)

### Alarm Configuration
To create an alarm, define:
1. **Metric**
2. **Threshold**
3. **Evaluation period**

---

### Alarm States (MEMORIZE)
- **OK**
- **ALARM**
- **INSUFFICIENT_DATA**

---

### Alarm Actions
When triggered, alarms can:
- Send SNS notifications
- Trigger Auto Scaling
- Reboot EC2 instances
- Invoke AWS Lambda

---

## Alarms + Logs (EXAM FAVORITE PATTERN)
- Logs → Metric filters
- Metric filters → Metrics
- Metrics → Alarms
- Alarms → Actions

### Example
- Detect HTTP 500 errors
- Trigger alarm if > threshold
- Send notification or auto-remediate

---

## Automated Remediation (EXAM GOLD)
CloudWatch alarms can trigger:
- EC2 recovery or reboot
- Scaling events
- SNS → Lambda → AWS API calls

➡️ Enables **self-healing architectures**

---

## Exam Takeaway Summary
- CloudWatch centralizes monitoring
- Basic = 5 min, Detailed = 1 min
- Namespaces group metrics
- Dimensions filter metrics
- Custom metrics = app-level visibility
- Logs + alarms = proactive & automated response
