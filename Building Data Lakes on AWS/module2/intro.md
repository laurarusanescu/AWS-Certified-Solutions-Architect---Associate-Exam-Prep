# Module 2: Data Ingestion, Cataloging, and Preparation — Notes

---

## Data Lake Architecture Layers (RECAP)
Most data lake architectures include the following layers:

1. **Data Sources**
2. **Data Ingestion**
3. **Data Storage**
4. **Cataloging & Processing**
5. **Search & Analytics**
6. **Visualization** (optional)

➡️ All data lakes must have:
- Ingestion
- Storage
- Cataloging
- Processing

Visualization may be optional.

---

## Focus of Module 2
This module concentrates on the **core middle layers** of a data lake:

- Data ingestion
- Data storage
- Data cataloging
- Data processing
- Querying data

---

## Key Topics Covered in Module 2 (EXAM & PRACTICAL)

### 1. Data Ingestion & Storage Relationship
- How data is ingested into AWS
- Choosing the **right storage layer** for data lakes
- Best practices for storing “data lake data” in the cloud
- Emphasis on **Amazon S3** as the primary data lake storage

---

### 2. Data Optimization Techniques (VERY IMPORTANT)
Three critical concepts for performance and cost optimization:

- **Data formatting**
- **Partitioning**
- **Compression**

➡️ These directly impact:
- Query performance
- Storage cost
- Analytics efficiency

---

### 3. AWS Glue Crawlers
- What AWS Glue Crawlers are
- How they:
  - Scan data in storage (e.g., S3)
  - Infer schemas automatically
  - Populate the **AWS Glue Data Catalog**
- Enable **schema-on-read**
- Reduce manual effort in data discovery

---

### 4. Security Policies in Data Lakes
- Controlling access to data
- Applying security and governance policies
- Ensuring:
  - Data protection
  - Proper authorization

---

### 5. Querying Data with Amazon Athena
- Use **Amazon Athena** to query data in S3
- Serverless, SQL-based querying
- Uses the **AWS Glue Data Catalog**
- No infrastructure to manage

---

## Why This Module Matters
- Handles **large-scale datasets**
- Optimizes for:
  - High performance
  - Low cost
- Makes data:
  - Discoverable
  - Queryable
  - Secure

---

## Module 2 Takeaway Summary
- Data lakes follow layered architectures
- Module 2 focuses on ingestion → storage → catalog → query
- Formatting, partitioning, and compression are key optimizations
- AWS Glue simplifies schema discovery
- Athena enables serverless analytics
