# Modern Data Architectures on AWS — Notes

---

## What Defines a Modern Data Architecture
Modern data architectures focus on:
- **Scalability**
- **Purpose-built analytics services**
- **Unified data access**
- **Governance**
- **High performance**
- **Cost efficiency**

The goal is to manage and analyze data **securely, efficiently, and at scale**.

---

## 1. Scalable Data Lakes
Focused on **secure storage** and **metadata management** for diverse datasets.

Key AWS services:
- **Amazon S3** – scalable, durable storage foundation
- **AWS Lake Formation** – data lake setup, governance, and security
- **Amazon Athena** – serverless SQL querying directly on S3

---

## 2. Purpose-Built Analytics Services
Use the **right tool for the right job**, instead of one system for everything.

### Databases
- **Amazon Aurora** – relational workloads
- **Amazon DynamoDB** – NoSQL, key-value access

### Search
- **Amazon OpenSearch Service** – full-text search and log analytics

### Big Data Processing
- **Amazon EMR (Elastic MapReduce)** – Spark, Hadoop, big data workloads

### Data Warehousing
- **Amazon Redshift** – analytical data warehouse

### Machine Learning
- **Amazon SageMaker** – build, train, and deploy ML models

### Streaming & Real-Time Analytics
- **Amazon MSK** – managed Apache Kafka
- **Amazon Kinesis Data Analytics** – real-time stream analytics

---

## 3. Unified Data Access
Access data **where it lives**, moving it only when necessary.

Key AWS services:
- **AWS Glue** – ETL and data integration
- **Amazon Kinesis Data Firehose** – streaming ingestion
- **AWS Database Migration Service (DMS)** – database replication and migration
- **AWS Transfer Family** – managed file transfers (SFTP, FTPS)
- **Amazon MSK** – Kafka-based streaming
- **Amazon AppFlow** – SaaS data ingestion (Salesforce, etc.)

---

## 4. Unified Governance
Concerned with **authorization, access control, and auditing**.

Primary service:
- **AWS Lake Formation**
  - Centralized governance
  - Fine-grained permissions
  - Secure data sharing
  - Auditing and access control

---

## 5. Performance & Cost Effectiveness
Achieve high performance **without overspending**.

Best practices:
- Use **columnar data formats** (Parquet, ORC)
- Apply **data compression**
- **Partition data** by common query fields
- Monitor costs and set **billing alerts**
- Optimize queries to reduce data scanned

---

## Summary: Modern Data Architecture on AWS
A modern AWS data architecture:
- Uses **S3-based data lakes** for scale
- Leverages **purpose-built analytics services**
- Enables **unified access** across data sources
- Enforces **centralized governance**
- Optimizes for **performance and cost**

---

## Exam Takeaway Summary
- One size does not fit all in analytics
- S3 + Lake Formation form the data lake core
- Purpose-built services improve efficiency
- Governance is essential for scale
- Optimization techniques reduce cost
