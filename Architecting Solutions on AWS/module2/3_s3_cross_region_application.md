# Amazon S3 Cross-Region Replication (CRR) & Lifecycle — Notes

---

# Amazon S3 Cross-Region Replication (CRR)

## What Is S3 CRR? (EXAM CRITICAL)
S3 Cross-Region Replication (CRR):
- Automatically replicates objects
- Replicates metadata and object tags
- Replicates across **different AWS Regions**

---

## What Can Be Replicated?
- Entire bucket
- Specific prefixes
- Specific objects (using object tags)

---

## Why Use CRR?

### 1. Compliance
- Regulatory requirements may demand:
  - Data stored far apart geographically
- CRR helps meet:
  - Data residency requirements
  - Cross-border storage mandates

---

### 2. Disaster Recovery
- Protect against regional failures
- Maintain secondary copy in another Region

---

### 3. Reduced Latency
- Keep copies closer to global users
- Improve access speed in multiple Regions

---

### 4. Regional Efficiency
- Multiple compute clusters in different Regions
- Each cluster reads from a local copy

---

### 5. Account Ownership Change
- Replicated objects can change ownership
- Protects against accidental deletion

---

## Key CRR Characteristics
- Source bucket → Destination bucket (different Region)
- Asynchronous replication
- Requires versioning enabled
- Must configure IAM permissions

---

# Amazon S3 Lifecycle Policies

## What Is S3 Lifecycle?
Lifecycle rules:
- Automatically transition objects between storage classes
- Automatically expire (delete) objects

---

## Common Lifecycle Use Cases

### Transition to Standard-IA
- For infrequently accessed objects

### Transition to S3 Glacier
- For archive storage
- Lower cost, slower retrieval

---

# S3 Intelligent-Tiering (EXAM FAVORITE)

## What Is Intelligent-Tiering?
- Automatically moves objects between access tiers
- Based on access patterns
- Designed for unknown or unpredictable workloads

---

## Why Use Intelligent-Tiering?
- Ideal for:
  - Data lakes
  - Analytics
  - New applications
  - User-generated content
- No performance impact
- No manual tiering

---

## Key Features
- Small monthly monitoring fee
- No retrieval charges
- No minimum retention period
- Objects <128 KB:
  - Not eligible for automatic tiering
  - Always charged at Frequent Access rates

---

# Amazon S3 Glacier Storage Classes

## Purpose
- Long-term archival storage
- Very low cost
- 11 nines durability

---

## Best For
- Historical logs
- Compliance archives
- Backup retention
- Rarely accessed data

---

# Comparing S3 Storage Strategies

| Feature | CRR | Lifecycle | Intelligent-Tiering |
|----------|------|------------|----------------------|
| Purpose | Regional replication | Storage class automation | Auto tiering |
| Disaster recovery | ✔ | ❌ | ❌ |
| Cost optimization | ❌ | ✔ | ✔ |
| Latency optimization | ✔ | ❌ | ❌ |
| Archive management | ❌ | ✔ | ✔ |

---

# Week 2 Relevance (Clickstream Scenario)

Customer Requirements:
- Cross-region backup → Use CRR
- Cost optimization → Use Lifecycle policies
- Unknown access patterns → Use Intelligent-Tiering
- Encryption → S3 supports encryption at rest & in transit

---

# Exam Takeaway Summary

- CRR = cross-region replication
- Lifecycle = automated storage transitions
- Intelligent-Tiering = automatic cost optimization
- Glacier = archival storage
- Versioning required for replication
- S3 durability = 11 nines
