# Data Lake vs Data Warehouse — Exam Notes

---

## High-Level Difference (EXAM CRITICAL)

| Concept | Data Warehouse | Data Lake |
|------|---------------|-----------|
| Type | Relational database | Non-relational data repository |
| Data Format | Structured only | Structured, semi-structured, unstructured |
| Schema | Schema-on-write | Schema-on-read |
| Purpose | Business analytics | Advanced analytics & ML |

---

## What Is a Data Warehouse?
- A **relational database**
- Stores **structured data only**
- Data must conform to a **predefined schema**
- Schema is enforced **before data is written**

➡️ Data is **cleaned, transformed, and modeled upfront**

---

## What Is a Data Lake?
- A **central repository** for data of any type
- Accepts data from:
  - IoT devices
  - Logs
  - Social media
  - Applications
- Stores data **as-is**
- Structure is applied **when data is read**

➡️ Store first, analyze later

---

## Schema-on-Write vs Schema-on-Read (EXAM FAVORITE)

### Schema-on-Write (Data Warehouse)
- Define schema **before ingestion**
- Strong data consistency
- Less flexibility
- Faster queries once data is loaded

---

### Schema-on-Read (Data Lake)
- No schema required at ingestion
- Schema applied during analysis
- Very flexible
- Requires governance to avoid chaos

---

## Cost Model Differences (EXAM CRITICAL)

### Data Warehouse Costs
- Pay to:
  - Keep the database running
  - Store data
  - Maintain performance
- Higher cost for:
  - Large scale
  - High performance

---

### Data Lake Costs
- Pay for:
  - Low-cost storage (e.g., Amazon S3)
  - Compute **only when analyzing**
- Much more cost-effective at scale

---

## Data Quality & Governance

### Data Warehouse
- High data quality
- Strong guardrails
- Single source of truth
- Data consistency enforced by design

---

### Data Lake
- Data quality varies
- Risk of **data swamp**
- Requires:
  - Cataloging
  - Governance
  - Access control

---

## Who Uses Each? (EXAM FAVORITE)

### Data Warehouse Users
- Business analysts
- BI teams
- Executives
- Use cases:
  - Dashboards
  - Reports
  - KPIs

---

### Data Lake Users
- Data scientists
- Data engineers
- ML engineers
- Use cases:
  - Machine learning
  - Predictive analytics
  - Data exploration
  - Model training

---

## Use Case Comparison

| Use Case | Best Choice |
|-------|-------------|
| BI reporting | Data Warehouse |
| Dashboards | Data Warehouse |
| ML / AI | Data Lake |
| Log analytics | Data Lake |
| IoT data | Data Lake |
| Structured financial data | Data Warehouse |

---

## Key Exam Insight
- **Neither is “better”**
- They solve **different problems**
- Often used **together**
  - Data lake feeds curated data into a warehouse

---

## Exam Takeaway Summary
- Data warehouse = structured, curated, BI-focused
- Data lake = flexible, scalable, analytics-focused
- Schema-on-write vs schema-on-read is the key difference
- Choose the tool based on **use case**, not preference
