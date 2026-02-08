# AWS Glue Jobs & Workflows — Notes

---

## AWS Glue Job Terminology (EXAM CRITICAL)
- When AWS Glue runs an ETL workload, it is called an **AWS Glue job**
- A Glue job performs:
  - Extract
  - Transform
  - Load (ETL)

➡️ Glue jobs are the **execution units** of data processing in AWS Glue

---

## Ways to Run AWS Glue Jobs (EXAM FAVORITE)

### 1. Scheduled Runs
- Jobs run at a specific time or interval
- Example:
  - Every Tuesday at 1:00 PM
- Useful when:
  - Data arrives on a known schedule
  - Processing is not time-sensitive

---

### 2. On-Demand Runs
- Jobs run **only when manually triggered**
- Useful for:
  - One-time processing
  - Infrequent datasets
  - Backfills or large historical loads

---

### 3. Conditional (Event-Based) Runs
- Jobs run when an **event occurs**
- Example:
  - New data arrives in an Amazon S3 bucket
- Often triggered using:
  - AWS Lambda
  - Event notifications

➡️ Ideal for **automated, data-driven pipelines**

---

## Why AWS Glue Workflows Are Needed
- Real data pipelines often require:
  - Multiple Glue jobs
  - Multiple steps
  - Dependencies between steps

➡️ Managing jobs individually does not scale

---

## AWS Glue Workflows (EXAM CRITICAL)

### What Is an AWS Glue Workflow?
- A way to **orchestrate multiple Glue components**
- Allows you to:
  - Chain jobs
  - Control execution order
  - Manage dependencies
  - Visualize pipeline progress

---

## Components of a Glue Workflow

### Triggers
- Define **when** a workflow or job starts
- Can be:
  - Scheduled
  - On-demand
  - Event-based

---

### Jobs
- ETL steps within the workflow
- Each job performs a specific task
- Examples:
  - Deduplication
  - Data standardization
  - Format conversion

---

### Crawlers
- Update the AWS Glue Data Catalog
- Run after transformations complete
- Ensure schemas stay current

---

## Example Glue Workflow (EXAM SCENARIO)
1. Trigger detects new data in S3
2. Glue Job #1:
   - Deduplicates data
3. Glue Job #2:
   - Fixes formatting issues (e.g., phone numbers)
4. Glue Crawler:
   - Updates Data Catalog tables
5. Data is ready for querying

➡️ This produces **clean, discoverable data**

---

## Visual Monitoring & Troubleshooting
- Glue workflows are **visualized in the AWS Console**
- You can:
  - See job execution order
  - Identify failures
  - Track success states

➡️ Green = success  
➡️ Red = failure

---

## Benefits of AWS Glue Workflows
- Simplifies complex pipelines
- Improves reliability
- Enhances observability
- Reduces manual intervention
- Encourages modular ETL design

---

## When to Use Glue Jobs vs Glue Workflows

| Use Case | Glue Job | Glue Workflow |
|-------|---------|---------------|
| Single ETL step | ✔ | ❌ |
| Multiple dependent steps | ❌ | ✔ |
| Complex pipelines | ❌ | ✔ |
| Visualization of flow | ❌ | ✔ |

---

## Exam Takeaway Summary
- Glue jobs execute ETL logic
- Jobs can be scheduled, on-demand, or event-driven
- Glue workflows orchestrate multiple jobs
- Workflows include triggers, jobs, and crawlers
- Visual workflows simplify monitoring and debugging
