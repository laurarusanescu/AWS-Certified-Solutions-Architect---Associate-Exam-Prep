# Amazon Relational Database Service (RDS) — Exam Notes

---

## What Is Amazon RDS? (EXAM CRITICAL)
**Amazon RDS** is a **managed relational database service** that removes the operational burden of database management.

AWS handles:
- Provisioning
- Patching
- Scaling
- Backups
- Recovery
- High availability

➡️ You focus on **application logic and data**, not infrastructure.

---

## Supported Amazon RDS Engines (MEMORIZE)

### Commercial
- Oracle
- SQL Server

### Open Source
- MySQL
- PostgreSQL
- MariaDB

### Cloud-Native
- **Amazon Aurora**
  - MySQL- and PostgreSQL-compatible
  - Higher performance, durability, and availability
  - Built for the cloud

---

## RDS Architecture: DB Instances

### What Is a DB Instance?
- A **DB instance** runs the database engine
- Can host:
  - Multiple databases
  - Multiple tables per database
- Runs on:
  - An **EC2 instance managed by RDS**
- Managed via:
  - **RDS Console**, not EC2 Console

---

## DB Instance Types (EXAM DETAIL)

### Instance Families
- **Standard** (general purpose)
- **Memory Optimized**
- **Burstable Performance**

➡️ Availability depends on the database engine

---

## RDS Storage (EXAM FAVORITE)
RDS uses **Amazon EBS** for storage.

### Storage Types
- General Purpose SSD
- Provisioned IOPS SSD
- Magnetic storage (❌ not recommended)

---

## RDS in a VPC (EXAM CRITICAL)

### DB Subnet Group
Defines where RDS instances run.

You must choose:
- Multiple **Availability Zones**
- **Private subnets** in those AZs

➡️ Databases should **not be publicly accessible**

---

### Network Security
- **Security Groups**
- **Network ACLs**

➡️ Only backend application instances should access the database

---

## IAM and RDS Security
- IAM policies control:
  - Who can create, modify, delete RDS resources
- Network controls handle:
  - Traffic flow
- IAM ≠ network security

---

## Backups in Amazon RDS (EXAM CRITICAL)

### Automated Backups
- Enabled **by default**
- Backup:
  - Entire DB instance
  - Transaction logs
- Retention:
  - **0–35 days**
- Backup window:
  - Configurable
  - Best during low activity

⚠️ Setting retention to **0 disables backups** and deletes existing ones

---

### Point-in-Time Recovery (EXAM FAVORITE)
- Restores data to a **specific second**
- Creates a **new DB instance**
- Uses:
  - Automated backups
  - Transaction logs

---

### Manual Snapshots
- Initiated manually
- Retained **until deleted**
- Used for:
  - Long-term retention
  - Compliance requirements

➡️ Restoring creates a **new DB instance**

---

### Backup Best Practice (EXAM RULE)
> Use **both** automated backups and manual snapshots

---

## High Availability with RDS Multi-AZ (EXAM GOLD)

### What Is Multi-AZ?
- Creates:
  - **Primary DB** in one AZ
  - **Standby DB** in another AZ
- Data replication:
  - **Synchronous**

---

### Multi-AZ Behavior
- Applications connect via:
  - A **single DNS endpoint**
- Standby DB:
  - Not readable
  - Not queried
- Automatic failover occurs if:
  - Primary DB fails

---

### Failover Process
1. Standby promoted to primary
2. DNS updated automatically
3. New standby created to maintain redundancy

➡️ Application does **not** change connection string

---

## Multi-AZ Subnet Requirement
- Subnets must be in:
  - **Different Availability Zones**
- This is why:
  - DB subnet groups span multiple AZs

---

## Exam Takeaway Summary
- RDS = managed relational database
- DB instances run on managed EC2
- Always deploy RDS in **private subnets**
- Automated backups = PITR
- Manual snapshots = long-term retention
- Multi-AZ = high availability, not read scaling
- Aurora = cloud-optimized RDS engine
