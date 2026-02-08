# Data Ingestion in Data Lakes — Notes

---

## What Is Data Ingestion? (EXAM CRITICAL)
**Data ingestion** is the process of **collecting data from source systems and loading it into a data lake**.

➡️ It is the **first step** in any data lake architecture.

---

## Purpose of Data Ingestion
Data ingestion enables you to:
- Continuously feed data into the data lake
- Centralize data from many sources
- Prepare data for:
  - Cataloging
  - Processing
  - Analytics
  - Machine learning

---

## Common Data Sources
Data can come from:
- Relational databases
- NoSQL databases
- IoT devices
- Mobile applications
- Logs
- Clickstream data
- Third-party systems
- Streaming platforms

➡️ Data lakes accept **any data type**.

---

## Types of Data Ingestion (EXAM FAVORITE)

### 1. Batch Ingestion
- Data is ingested in **chunks** at scheduled intervals
- Example:
  - Nightly database export
- Best for:
  - Historical data
  - Large but infrequent data transfers

---

### 2. Streaming Ingestion
- Data is ingested **continuously in real time**
- Example:
  - IoT sensor data
  - Application logs
- Best for:
  - Real-time analytics
  - Event-driven systems

---

## AWS Services for Data Ingestion (EXAM CRITICAL)

### AWS Database Migration Service (DMS)
- Used to:
  - Migrate databases into AWS
  - Replicate data continuously
- Supports:
  - Homogeneous migrations
  - Heterogeneous migrations
- Common target:
  - **Amazon S3 (data lake)**

---

### Amazon Kinesis
- Used for:
  - Real-time streaming ingestion
- Handles:
  - High-velocity data
- Common use cases:
  - Clickstream data
  - IoT data
  - Logs

---

### Other Ingestion Methods
- Application uploads directly to S3
- API-based ingestion
- File transfers (FTP → S3)

---

## Where Ingested Data Goes (EXAM FAVORITE)

### Amazon S3 — Primary Storage
- Most data lakes ingest data into:
  - **Amazon S3**
- Reasons:
  - Scalable
  - Durable
  - Cost-effective
  - Supports all data formats

---

## Raw Data Zone (IMPORTANT TERM)
- First landing place for ingested data
- Data is:
  - Unmodified
  - Unfiltered
  - Unprocessed

➡️ Also called:
- Landing zone
- Raw zone

---

## Characteristics of Raw Data
- Stored exactly as received
- Preserves original source
- Used for:
  - Reprocessing
  - Auditing
  - Data lineage

---

## Data Ingestion Best Practices (EXAM GOLD)
- Do **not** modify data during ingestion
- Store data in:
  - Source-based folders
  - Time-based partitions
- Ensure:
  - High availability
  - Fault tolerance
- Automate ingestion where possible

---

## Data Ingestion vs Data Processing
- **Ingestion**:
  - Moves data into the lake
- **Processing**:
  - Transforms data after ingestion

➡️ Keep these steps **separate**.

---

## Ingestion in the Data Lake Pipeline
1. Data sources generate data  
2. Ingestion services move data  
3. Data lands in **Amazon S3 (raw zone)**  
4. AWS Glue catalogs & processes data  
5. Athena queries data  
6. QuickSight visualizes results  

---

## Exam Takeaway Summary
- Data ingestion feeds the data lake
- Can be batch or streaming
- AWS DMS & Kinesis are key services
- Amazon S3 is the primary ingestion target
- Raw data is stored unchanged
