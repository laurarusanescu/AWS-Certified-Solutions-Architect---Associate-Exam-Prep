# Data Lake Ingestion & Pipeline Architecture — Exam Notes

---

## Goal: Filling the Data Lake
A data lake does not fill itself — you must build a **data ingestion pipeline**.

The purpose of the pipeline is to:
- Collect data from many sources
- Store it centrally
- Catalog and process it
- Query and analyze it for insights

---

## High-Level Data Lake Pipeline Flow (EXAM CRITICAL)

1. **Data Sources**
2. **Data Ingestion**
3. **Data Storage**
4. **Cataloging & Processing**
5. **Query & Analytics**
6. **Visualization**

---

## 1. Data Sources
Data can come from virtually anywhere:
- Existing databases
- IoT devices
- Mobile applications
- Logs
- Streaming data
- Third-party systems

➡️ Data lakes are designed to accept **any data type**

---

## 2. Data Ingestion (EXAM FAVORITE)
You need a service that **feeds data continuously** into AWS.

### Common AWS Ingestion Services
- **AWS Database Migration Service (DMS)**
  - Move existing databases into AWS
- **Amazon Kinesis**
  - Stream real-time data
- Combination of multiple ingestion tools

➡️ Ingestion can be **batch or streaming**

---

## 3. Data Storage
Once ingested, data must be stored.

### Storage Options
- **Amazon S3** (most common for data lakes)
- Databases
- Data warehouses (Amazon Redshift)

➡️ Choice depends on:
- Whether schema is required upfront
- Cost considerations
- Query patterns

---

## Raw Data (EXAM TERM)
- Data stored **exactly as received**
- No transformations
- No cleaning
- Also called:
  - *Raw zone*
  - *Landing zone*

➡️ “Pure source data”

---

## 4. Cataloging & Processing (EXAM CRITICAL)

### AWS Glue
AWS Glue performs multiple roles:
- **ETL (Extract, Transform, Load)**
- **Schema inference**
- **Data catalog creation**

---

### AWS Glue Crawlers
- Scan data stored in S3
- Automatically detect:
  - Schema
  - Data types
- Populate the **AWS Glue Data Catalog**

➡️ Enables **schema-on-read**

---

## Transformed Data (EXAM TERM)
- Data that has been:
  - Cleaned
  - Standardized
  - Optimized for querying
- Often stored in:
  - A separate S3 prefix
  - Or a separate S3 bucket

➡️ Also called:
- *Curated zone*
- *Processed zone*

---

## 5. Querying the Data (EXAM FAVORITE)

### Amazon Athena
- **Serverless SQL query engine**
- Queries data **directly in S3**
- Uses:
  - AWS Glue Data Catalog
- No infrastructure to manage

➡️ Pay only per query

---

## 6. Visualization & Analytics
After querying, results are visualized.

### Common Tools
- **Amazon QuickSight**
- Third-party BI tools

➡️ Used for:
- Dashboards
- Charts
- Business decision-making

---

## Basic Data Lake Architecture (EXAM GOLD)

### Simple, Valid, and Common Pattern
1. Data sources → ingest data
2. Raw data stored in S3
3. AWS Glue ETL jobs transform data
4. Glue crawlers build catalog
5. Athena queries curated data
6. QuickSight visualizes results

➡️ Simple ≠ bad  
➡️ Ideal starting architecture

---

## Key Terminology to Memorize
- **Raw data** → untouched source data
- **Transformed data** → cleaned and query-ready
- **Schema-on-read** → structure applied at query time
- **ETL** → extract, transform, load

---

## Exam Takeaway Summary
- Data lakes require ingestion pipelines
- Amazon S3 is the storage foundation
- AWS Glue = ETL + catalog
- Athena = serverless SQL on S3
- QuickSight = visualization
- Start simple, evolve over time
