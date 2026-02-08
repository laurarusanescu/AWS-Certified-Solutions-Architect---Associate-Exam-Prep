# Amazon DynamoDB — Exam Notes

---

## What Is Amazon DynamoDB? (EXAM CRITICAL)
**Amazon DynamoDB** is a **fully managed NoSQL key-value and document database** that provides:
- **Single-digit millisecond performance**
- **Seamless scalability**
- **High availability and durability**

AWS manages:
- Hardware provisioning
- Setup and configuration
- Replication
- Software patching
- Cluster scaling

➡️ You focus only on **data modeling and access patterns**

---

## Key DynamoDB Characteristics (MEMORIZE)
- Serverless (no servers to manage)
- Automatically scales **up and down**
- No downtime during scaling
- Predictable performance
- Data stored on **SSDs**
- Automatically replicated across **multiple AZs**
- Region-scoped service

---

## Core Components of DynamoDB (EXAM CRITICAL)

### Tables
- A **table** is a collection of items
- Example tables:
  - People
  - Cars
  - Orders

---

### Items
- An **item** is a single record in a table
- Similar to:
  - Rows / records
- Each item is:
  - Uniquely identifiable
- No limit to the number of items in a table

---

### Attributes
- An **attribute** is a piece of data in an item
- Similar to:
  - Columns / fields
- Schema is:
  - **Flexible**
  - Items can have different attributes

---

## Primary Keys (EXAM FAVORITE)

DynamoDB uses **primary keys** to uniquely identify items.

### Partition Key
- Single attribute
- Used to distribute data across partitions

---

### Composite Primary Key
- Partition key + sort key
- Allows:
  - Grouping related items
  - Querying ranges of data

---

## Secondary Indexes (EXAM CONCEPT)
- Provide **additional query flexibility**
- Allow querying on attributes that are **not part of the primary key**
- Types:
  - Global Secondary Index (GSI)
  - Local Secondary Index (LSI)

---

## Scalability & Performance (EXAM GOLD)
- DynamoDB automatically:
  - Spreads data across partitions
  - Distributes traffic to handle throughput
- Can handle:
  - Any amount of data
  - Any request volume

➡️ Scaling does **not** impact performance

---

## High Availability & Durability
- Data automatically replicated across:
  - **Multiple Availability Zones**
- Built-in:
  - Fault tolerance
  - High availability
- No manual replication required

---

## Security with DynamoDB (EXAM DETAIL)
- **Encryption at rest** enabled by default
- AWS manages encryption
- Integrates with:
  - IAM for access control

---

## DynamoDB vs Relational Databases (EXAM DECISION)

| Feature | DynamoDB | Relational DB |
|------|---------|---------------|
| Schema | Flexible | Fixed |
| Scaling | Automatic | Manual / limited |
| Joins | ❌ No | ✅ Yes |
| Performance | Predictable | Varies |
| Use Case | Massive scale | Transactions |

---

## Common DynamoDB Use Cases (EXAM FAVORITES)
- Serverless applications
- Microservices
- Key-value lookups
- High-traffic web applications
- Gaming leaderboards
- IoT data
- Session management

---

## When to Choose DynamoDB (EXAM RULE)
Choose DynamoDB when you need:
- Massive scale
- Low latency
- Flexible schema
- Fully managed NoSQL
- Serverless architecture

---

## When NOT to Choose DynamoDB
- Complex joins
- Relational queries
- Strong relational constraints
- Fixed schema with ACID transactions across many tables

---

## Exam Takeaway Summary
- DynamoDB = managed NoSQL
- Tables → Items → Attributes
- Flexible schema
- Primary keys are critical
- Auto-scaling & HA built-in
- Best for high-scale, low-latency workloads
