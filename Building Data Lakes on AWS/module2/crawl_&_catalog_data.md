# Data Discovery & Cataloging in Data Lakes — Notes

---

## What Is Data Cataloging? (EXAM CRITICAL)
**Data cataloging** is the process of **organizing, describing, and managing data** stored in a data lake.

Its goal is to transform:
- A chaotic collection of raw data  
➡️ into  
- A **well-organized, searchable, and governed resource**

---

## Why Data Cataloging Is Important
Without cataloging:
- Data is hard to find
- Data is hard to trust
- Costs increase (S3 charges per usage)
- The data lake becomes a **data swamp**

---

## Benefits of Data Cataloging (EXAM FAVORITE)
Cataloging adds:
- Discoverability
- Metadata management
- Data governance
- Better collaboration
- Improved efficiency
- Faster analytics

---

## AWS Glue — Core Data Catalog Service (EXAM CRITICAL)

### What Is AWS Glue?
**AWS Glue** is a managed AWS service that provides:
- A centralized **Data Catalog**
- Schema discovery
- Metadata management
- Data processing features (ETL)

---

## AWS Glue Data Catalog

### What Is the Glue Data Catalog?
- A **central metadata repository**
- Stores:
  - Table definitions
  - Schemas
  - Data locations
- Used by:
  - Amazon Athena
  - AWS Glue
  - Amazon Redshift Spectrum
  - Other analytics services

---

### Important Concept (EXAM GOLD)
⚠️ **AWS Glue Data Catalog does NOT store data**

- It stores **metadata only**
- Tables are **pointers** to data locations (e.g., S3)

➡️ Table property: **`location`**

---

## Glue Tables in Data Lakes
- Represent metadata about datasets
- Usually point to:
  - **Amazon S3 buckets**
- Can also point to:
  - Databases
  - NoSQL sources

---

## Why Tables Matter
- Tables allow:
  - Access control via AWS permissions
  - Joining data across different sources
  - Consistent querying

---

## AWS Glue Crawlers (EXAM FAVORITE)

### What Is a Glue Crawler?
A **Glue Crawler**:
- Scans data sources
- Infers schema
- Creates or updates tables in the Glue Data Catalog

➡️ Automates data discovery

---

### What Crawlers Do
1. Connect to data source
2. Analyze data structure
3. Infer schema
4. Populate or update catalog tables

---

## Supported Data Sources (EXAM DETAIL)

### Native Connections
- Amazon S3
- Amazon DynamoDB

---

### JDBC Connections
- Amazon RDS
- Amazon Aurora
- MySQL
- PostgreSQL
- Oracle
- Microsoft SQL Server
- MariaDB

---

### NoSQL Compatibility
- MongoDB
- Amazon DocumentDB (MongoDB compatibility mode)

---

## Schema Inference with Classifiers

### What Is a Classifier?
- Component that determines:
  - File format
  - Schema
- Used during crawler execution

---

### Built-In Classifiers
Support common formats:
- CSV
- JSON
- Apache Avro
- (and others)

---

### Custom Classifiers
- Used for:
  - Custom formats
  - Application-specific log files

---

## After a Crawler Runs
- Schema is discovered
- Glue Data Catalog tables are:
  - Created
  - Or updated
- Data becomes:
  - Discoverable
  - Queryable

---

## Why Glue Is Critical in Data Lakes
- Enables **schema-on-read**
- Reduces manual effort
- Prevents data swamp
- Makes analytics services work

---

## Exam Takeaway Summary
- Data cataloging organizes the data lake
- AWS Glue is the primary cataloging service
- Glue Data Catalog stores metadata, not data
- Crawlers automate schema discovery
- Tables point to data locations (usually S3)
- Classifiers infer data structure
