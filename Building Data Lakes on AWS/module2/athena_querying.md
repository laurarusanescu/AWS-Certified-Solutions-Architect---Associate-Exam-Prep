# Querying Data Lakes with Amazon Athena — Notes

## When Athena Is Used
- After data is ingested into the data lake
- After AWS Glue Crawlers infer schemas
- After tables exist in the AWS Glue Data Catalog

➡️ At this stage, the data is ready to be queried.

---

## What Is Amazon Athena? (EXAM CRITICAL)
- Serverless, interactive query service
- Queries data stored in **Amazon S3**
- Uses **standard SQL**
- No SDK or infrastructure management required

➡️ If you know SQL, you can use Athena.

---

## Serverless Characteristics
With Athena, you do **not** manage:
- Operating systems
- EC2 instances
- Networking
- Packages

You only need:
- Data in S3
- Tables in the AWS Glue Data Catalog
- IAM permissions to query

---

## Scalability & Pricing (EXAM FAVORITE)
- Athena scales automatically
- Pricing is **per amount of data scanned**
- More data scanned = higher cost

➡️ Optimization directly reduces cost.

---

## Supported Data Formats
- CSV
- JSON
- Apache Avro
- Apache ORC
- Apache Parquet

➡️ Columnar formats are strongly recommended.

---

## Why Optimization Matters for Athena
Because Athena charges per data scanned:
- Poorly optimized data = slow & expensive queries
- Optimized data = faster & cheaper queries

Best practices:
- Columnar formats
- Partitioning
- Compression

➡️ Can reduce query cost by up to **90%**.

---

## Athena & AWS Glue Relationship (EXAM GOLD)
- Athena uses the **AWS Glue Data Catalog**
- Glue tables define:
  - Schema
  - Data location
- Tables contain **metadata only**, not data

➡️ Deleting a table does **not** delete the underlying data.

---

## Table Location Concept
- Every table has a **location**
- Location points to:
  - Amazon S3
  - Amazon DynamoDB
  - Other supported sources

➡️ Table = schema + pointer to data.

---

## Federated Queries (EXAM CONCEPT)
- Athena supports **federated queries**
- Allows querying and joining data from:
  - S3
  - External data sources
- Eliminates the need to copy data into S3

---

## Integrations (EXAM FAVORITE)

### Athena + AWS Lambda
- Queries can be triggered by:
  - Scheduled events
  - APIs
  - Event-driven workflows

### Athena + Amazon QuickSight
- Used for data visualization
- Dashboards always reflect the latest data
- Queries run on demand

---

## Security & Access Control
- Controlled using **IAM**
- Permissions required for:
  - Athena queries
  - Access to underlying S3 data

---

## Key Advantages of Athena
- Serverless
- SQL-based
- Highly scalable
- Cost-efficient when optimized
- Tight integration with S3 and AWS Glue

---

## Exam Takeaway Summary
- Athena = SQL querying on S3
- Serverless and auto-scaling
- Pay per data scanned
- Optimization is critical for cost control
- Glue provides schema, not data
- Federated queries enable cross-source analytics
