# EC2 Instance Storage & Amazon EBS — Exam Notes

## Amazon EC2 Instance Store

### What Is Instance Store?
- **Temporary (ephemeral) block storage**
- Physically attached to the **EC2 host**
- **Lifecycle tied to the EC2 instance**

➡️ If the instance is stopped, terminated, or fails → **data is lost**

---

### Key Characteristics (EXAM CRITICAL)
- Very **high performance**
- **No data persistence**
- Cannot be detached or reattached
- Ideal for short-lived data

---

### Common Use Cases
- Caches
- Buffers
- Scratch data
- Temporary files
- Distributed systems that replicate data (e.g. Hadoop)

---

### Exam Rule
> **Never store critical or long-term data on Instance Store**

---

## Amazon Elastic Block Store (EBS)

### What Is Amazon EBS?
- **Persistent block storage** for EC2
- Storage units are called **EBS volumes**
- Similar to an **external hard drive**
- Exists **independently** of the EC2 instance

---

### Key Characteristics (EXAM CRITICAL)
- Data **persists** even if the instance stops or terminates
- Volumes are **AZ-scoped**
- Can be:
  - Detached
  - Reattached to another EC2 instance (same AZ)

---

### EC2 ↔ EBS Relationship
- One EC2 instance → **many EBS volumes**
- Most EBS volumes:
  - Attach to **one instance at a time**
- **EBS Multi-Attach**:
  - Limited support
  - Same AZ
  - Not all instance types

---

## Scaling Amazon EBS Volumes

### Scaling Options
1. **Increase volume size**
   - Up to **16 TB per volume**
2. **Attach multiple volumes**
   - Combine storage across volumes

---

## Amazon EBS Use Cases (EXAM FAVORITES)
- Root/boot volumes (EBS-backed AMIs)
- Databases
- Enterprise applications
- Throughput-intensive workloads

---

## Amazon EBS Volume Types (MEMORIZE)

### SSD Volumes (Random I/O)

#### Provisioned IOPS SSD
- Highest performance
- Use cases:
  - I/O-intensive databases
- Max IOPS: **64,000**
- Max throughput: **1,000 MB/s**

---

#### General Purpose SSD
- Balanced price & performance
- Use cases:
  - Boot volumes
  - Dev/Test
  - Interactive apps
- Max IOPS: **16,000**
- Max throughput: **250 MB/s**

---

### HDD Volumes (Sequential I/O)

#### Throughput Optimized HDD
- Low-cost, high throughput
- Use cases:
  - Big data
  - Data warehouses
  - Log processing
- Max throughput: **500 MB/s**

---

#### Cold HDD
- Lowest cost
- Use cases:
  - Infrequently accessed data
- Max throughput: **250 MB/s**

---

## EBS Volume Categories (EXAM RULE)
- **SSD** → random I/O, low latency
- **HDD** → sequential I/O, large throughput

---

## Benefits of Amazon EBS (EXAM GOLD)
- High availability (replicated within AZ)
- Persistent storage
- Encryption supported
- On-the-fly scaling
- Snapshot backups

---

## EBS Snapshots (EXAM CRITICAL)

### What Is an EBS Snapshot?
- **Backup of an EBS volume**
- Stored in **Amazon S3**
- Managed via EC2 console

---

### Snapshot Characteristics
- **Incremental**
  - Only changed blocks are saved
- Highly durable
- Stored across **multiple AZs**

---

### Snapshot Use Cases
- Backup and recovery
- Create new volumes
- Copy volumes across AZs

---

### Snapshot Exam Rule
> Snapshots are **incremental**, but restoring creates a **full volume**

---

## Instance Store vs EBS (EXAM COMPARISON)

| Feature | Instance Store | EBS |
|------|---------------|-----|
| Persistence | ❌ No | ✅ Yes |
| Performance | Very high | High |
| Lifecycle | Tied to EC2 | Independent |
| Detachable | ❌ No | ✅ Yes |
| Use Case | Temporary data | Long-term data |

---

## Exam Takeaway Summary
- Instance Store = fast, temporary
- EBS = persistent block storage
- Use SSD for random I/O
- Use HDD for sequential I/O
- Always snapshot critical EBS data
