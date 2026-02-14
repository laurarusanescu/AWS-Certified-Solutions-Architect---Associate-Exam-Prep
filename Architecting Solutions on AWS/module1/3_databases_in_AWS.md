# Databases on AWS — Architecture Decision Notes

---

## Purpose-Built Databases on AWS (EXAM CRITICAL)

AWS databases are **purpose-built**, meaning:
- Each database service is optimized for specific workloads
- Choose the database that best fits the use case
- Avoid using relational databases for everything (legacy mindset)

➡️ Modern architecture = right database for the right job

---

## Why Database Choice Matters
Choosing the correct database:
- Reduces development effort
- Minimizes operational overhead
- Improves performance
- Optimizes cost

---

# Why DynamoDB Was Chosen for This Use Case

For the Orders Service:

- Used as a **simple lookup table**
- No need for:
  - Complex SQL joins
  - Relational queries
- Workload is:
  - Spiky
  - Requires automatic scaling
- Customer prefers:
  - Serverless
  - Low operational overhead

➡️ DynamoDB fits these requirements perfectly

---

# Amazon DynamoDB (EXAM CRITICAL)

## What Is DynamoDB?
- Fully managed **NoSQL database**
- Key-value and document model
- Serverless
- Highly scalable
- Highly available

---

## Key Benefits
- Automatic scaling
- No infrastructure management
- Encryption at rest
- Handles virtually unlimited traffic
- Minimal downtime during scaling

---

## Core Components
- **Tables**
- **Items**
- **Attributes**
- **Primary keys**
- **Secondary indexes**
- **DynamoDB Streams** (for event-driven processing)

---

## When to Use DynamoDB
- Simple lookup patterns
- High-throughput workloads
- Spiky traffic
- Serverless architectures
- Event-driven systems

---

# Amazon Aurora (Not Chosen Here)

## What Is Aurora?
- Fully managed relational database
- Compatible with:
  - MySQL
  - PostgreSQL
- Part of Amazon RDS

---

## Key Strengths
- Enterprise-grade relational database
- High performance:
  - Up to 5x MySQL throughput
- Automatic storage scaling (up to 128 TiB)
- Built-in replication and clustering

---

## Aurora Serverless v2
- Automatic capacity scaling
- Pay only for resources used
- Ideal for:
  - Variable workloads
  - Dev/test environments
  - Multitenant systems

---

## Why Aurora Was Not Chosen
- Customer does not require:
  - Complex relational features
  - Joins across multiple tables
- Simpler NoSQL model is sufficient
- DynamoDB reduces operational complexity further

---

# Amazon RDS Proxy (EXAM CONCEPT)

## What Is RDS Proxy?
- Connection pooling service for RDS/Aurora
- Improves scalability and resilience

---

## Benefits
- Reuses connections to reduce overhead
- Handles traffic spikes
- Automatically fails over to standby DB
- Integrates with:
  - IAM authentication
  - AWS Secrets Manager

---

## When to Use RDS Proxy
- Applications with:
  - Frequent connection creation
  - High concurrency
  - Database connection bottlenecks

---

# Comparing DynamoDB vs Aurora (EXAM FAVORITE)

| Feature | DynamoDB | Aurora |
|----------|-----------|--------|
| Database Type | NoSQL | Relational |
| Scaling | Automatic & serverless | Managed, scalable |
| SQL Support | No | Yes |
| Joins | No | Yes |
| Operational Overhead | Very low | Low |
| Best For | Simple lookup, spiky workloads | Complex relational workloads |

---

# Architecture Takeaway for This Use Case

Requirements:
- Spiky demand
- Minimal operational overhead
- Simple data model
- High availability
- Durable storage

➡️ **DynamoDB is the best fit**

---

## Exam Takeaway Summary
- Use purpose-built databases
- DynamoDB = serverless, scalable, simple
- Aurora = relational, enterprise-grade
- RDS Proxy improves relational scaling
- Choose based on workload, not familiarity
