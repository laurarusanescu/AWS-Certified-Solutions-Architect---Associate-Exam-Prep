# Architecture Optimizations for Week 1 — Notes

This reading focuses on **performance and cost optimizations** for:
- Amazon DynamoDB
- AWS Lambda

---

# 1️⃣ Optimizing Amazon DynamoDB

## DynamoDB Accelerator (DAX) (EXAM FAVORITE)

### What Is DAX?
- Fully managed, highly available, in-memory cache for DynamoDB
- Improves performance:
  - From milliseconds
  - To microseconds
- Supports millions of requests per second

---

### Why Use DAX?
- Up to 100x performance improvement
- No cache management required:
  - No manual invalidation
  - No cluster management
- Compatible with existing DynamoDB API calls
- No changes to application logic required

---

### Networking Requirements
- Runs inside an **Amazon VPC**
- Access controlled via:
  - VPC security groups

---

### When to Use DAX
- High read workloads
- Microsecond latency requirements
- Frequently accessed data
- Caching repetitive lookups

---

# 2️⃣ Optimizing AWS Lambda

---

## AWS Lambda Power Tuning (EXAM CONCEPT)

### What It Is
- Open-source tool
- Uses AWS Step Functions
- Helps determine optimal memory configuration

---

### Why It Matters
Lambda pricing depends on:
- Memory allocated
- Execution duration

Increasing memory:
- Increases CPU
- May reduce execution time
- Sometimes lowers total cost

---

### Optimization Strategies
- Cost optimized
- Speed optimized
- Balanced

---

### How It Works
1. Provide Lambda ARN
2. Tool tests multiple memory sizes (128MB–10GB)
3. Analyzes execution logs
4. Suggests best configuration
5. Produces cost vs performance visualization

---

### Key Insight
More memory can:
- Reduce runtime
- Reduce cost
- Improve performance

---

## AWS Lambda Powertools

### What It Is
- Utility toolkit for Lambda
- Encourages best practices

---

### Key Features
- Structured logging
- Distributed tracing
- Custom metrics
- Idempotency handling
- Batch processing utilities

---

### Why It Matters
Improves:
- Observability
- Reliability
- Maintainability

---

## Lambda Execution Environment Reuse (EXAM FAVORITE)

### What It Is
Lambda may reuse execution environments across invocations.

---

### Optimization Strategy
Move initialization logic **outside the handler**, such as:
- SDK clients
- Database connections
- Static assets

Store temporary assets in:
- `/tmp` directory

---

### Benefits
- Reduced cold start overhead
- Faster execution
- Lower cost

---

### Security Warning
Do NOT:
- Store user data in memory
- Store sensitive state across invocations

If state is required:
- Use separate functions
- Use separate versions

---

# Summary of Week 1 Optimizations

## DynamoDB
- Use **DAX** for microsecond latency
- Use VPC security groups for access control

---

## Lambda
- Use **Power Tuning** for cost/performance optimization
- Use **Powertools** for best practices
- Use **execution environment reuse** for speed

---

## Architecture Pillars Reinforced
- Performance efficiency
- Cost optimization
- Operational excellence
- Security

---

## Exam Takeaway Summary

- DAX = in-memory cache for DynamoDB
- Lambda memory affects CPU and cost
- More memory can reduce total cost
- Power Tuning uses Step Functions
- Execution reuse reduces cold start overhead
- Powertools improves observability and resilience
