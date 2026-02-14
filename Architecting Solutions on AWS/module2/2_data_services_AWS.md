# A Look into AWS Data Services — Notes

---

## Clickstream Data (EXAM CONCEPT)

Clickstream data:
- Small, continuous events
- High speed and high volume
- Generated mostly by frontend systems
- Represents user interactions

Examples:
- Menu item viewed
- Item expanded
- Item added to cart
- Time spent on a page

Used for:
- Behavior analysis
- Optimization
- Reporting
- Machine learning

---

# AWS Data Services Categories (EXAM CRITICAL)

AWS groups data services into four main categories:

1. Data Lakes & Storage
2. Data Analytics
3. Data Movement
4. Predictive Analytics & Machine Learning

---

# 1️⃣ Data Lakes & Storage

## Amazon S3
- Scalable object storage
- Foundation of most data lakes
- Used for:
  - Clickstream storage
  - Analytics datasets
  - Backup and restore
- Supports multiple storage classes
- 11 nines durability

Common use cases:
- Data lakes
- Static websites
- Archival storage
- Backup solutions

---

## Amazon S3 Glacier
- Purpose-built archival storage
- Extremely low cost
- Long-term retention
- 11 nines durability

Best for:
- Historical clickstream archives
- Compliance storage

---

## AWS Lake Formation
- Simplifies secure data lake setup
- Governance and fine-grained access control
- Integrates with:
  - S3
  - Glue
  - Athena

---

# 2️⃣ Data Analytics Services

## Amazon Athena
- Serverless SQL querying on S3
- Pay per data scanned
- No infrastructure management
- Ideal for ad hoc analytics

---

## Amazon EMR
- Big data processing (Spark, Hive, Presto)
- Petabyte-scale analytics
- Used for:
  - Complex transformations
  - Streaming pipelines
  - ML workloads

Not chosen in Week 2 scenario because:
- Higher operational complexity
- Requires big data expertise

---

## Amazon OpenSearch Service
- Log analytics
- Real-time monitoring
- Full-text search
- Successor to Elasticsearch Service

Best for:
- Search-heavy workloads
- Log analytics
- Real-time dashboards

---

# 3️⃣ Data Movement Services

## Amazon Kinesis
- Real-time streaming ingestion
- High-throughput event pipelines
- Ideal for clickstream ingestion

Includes:
- Kinesis Data Streams
- Kinesis Data Firehose
- Kinesis Data Analytics

---

## AWS Glue
- Serverless data integration
- ETL processing
- Data cataloging
- Schema inference

Used for:
- Data cleaning
- Transformation
- Loading data into S3, warehouses, etc.

---

## AWS Database Migration Service (DMS)
- Migrates databases to AWS
- Supports minimal downtime
- Useful for hybrid migrations

---

# 4️⃣ Predictive Analytics & Machine Learning

## Amazon SageMaker
- Fully managed ML platform
- Build, train, deploy ML models
- Serverless & scalable
- Requires ML knowledge

---

## Amazon Rekognition
- Pretrained computer vision APIs
- Detect objects, faces, attributes
- Serverless image/video analysis

Use case:
- Image analytics in data workflows

---

## Amazon Comprehend
- NLP service
- Extract insights from text
- Analyze sentiment, entities, key phrases

Includes:
- Amazon Comprehend Medical for healthcare text

---

# Architectural Insight

Modern data architecture principle:
> Use the **right tool for the right job**

For clickstream scenario:
- Ingestion → Kinesis
- Storage → S3
- Processing → Glue
- Querying → Athena
- Visualization → QuickSight
- ML (optional) → SageMaker

---

# Exam Takeaway Summary

- Clickstream = high-speed user event data
- S3 = data lake foundation
- Athena = serverless querying
- Kinesis = real-time ingestion
- Glue = ETL + catalog
- EMR = big data at scale
- SageMaker = ML platform
- OpenSearch = search & log analytics
- Purpose-built databases & analytics services matter
