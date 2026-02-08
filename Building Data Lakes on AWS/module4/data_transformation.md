# Data Transformation in Data Lakes — AWS Glue & DataBrew Notes

---

## The Problem: Non-Uniform Data (EXAM CRITICAL)
When ingesting data from multiple sources, data often becomes:
- Inconsistent
- Messy
- Hard to analyze

### Common Issues
- Date formats differ by region (DD/MM/YYYY vs MM/DD/YYYY)
- Phone numbers use different formats
- Postal codes vary (letters vs numbers)
- Sensitive fields appear where they shouldn’t

➡️ This is normal — and unavoidable at scale.

---

## Why Data Transformation Matters
- Most data lakes mix data from **many sources**
- Data lake teams spend up to **80% of their time**:
  - Cleaning
  - Organizing
  - Standardizing data
- Transformation is a **continuous process**, not a one-time task

---

## What Is Data Transformation?
**Data transformation** is the process of:
- Cleaning data
- Standardizing formats
- Enforcing business rules
- Masking or removing sensitive information

➡️ Turns raw data into **usable, trusted data**

---

## AWS Glue — ETL Engine (EXAM CRITICAL)

### What Is AWS Glue?
- Fully managed **ETL (Extract, Transform, Load)** service
- Serverless
- Scales automatically
- No infrastructure to manage

---

### What AWS Glue Can Do
- Read raw data from S3 and other sources
- Clean and normalize data
- Apply transformations
- Write transformed data back to S3

➡️ Produces a **clean, analytics-ready dataset**

---

## Common AWS Glue Transformation Use Cases

### Data Standardization
- Normalize date formats
- Standardize phone numbers
- Normalize postal codes

---

### Data Privacy & Compliance (EXAM FAVORITE)
- Mask or remove sensitive fields:
  - Names
  - Email addresses
  - Tax IDs
  - IP addresses

➡️ Required for regulations (GDPR, privacy laws)

---

### Data Masking Example
- Remove last name
- Mask part of email
- Obscure sensitive identifiers

➡️ Glue automates this reliably

---

## Raw vs Transformed Data
- **Raw data**:
  - Original
  - Unmodified
  - Stored for audit & lineage
- **Transformed data**:
  - Cleaned
  - Secure
  - Ready for analytics & visualization

---

## AWS Glue DataBrew (EXAM CONCEPT)

### What Is DataBrew?
- **Point-and-click data transformation tool**
- Built on AWS Glue
- Designed for:
  - Analysts
  - Data engineers
  - Non-developers

---

### Key DataBrew Features
- 250+ prebuilt transformations
- No coding required
- Serverless & auto-scaling
- Ideal for data preparation

---

### When to Use DataBrew
- You want visual, interactive transformations
- You don’t want to write ETL code
- You need fast data cleanup

---

## AWS Glue vs DataBrew

| Feature | AWS Glue ETL | Glue DataBrew |
|------|-------------|---------------|
| Coding | Yes | No |
| UI-based | No | Yes |
| Transformations | Custom | Prebuilt |
| Scalability | Serverless | Serverless |

---

## Typical Data Transformation Flow
1. Raw data ingested into S3
2. AWS Glue ETL or DataBrew processes data
3. Sensitive data masked or removed
4. Clean data written to a new S3 location
5. Data ready for analytics & visualization

---

## Why This Matters for Analytics
- Clean data:
  - Produces accurate insights
  - Reduces query errors
  - Improves trust in dashboards
- Enables:
  - BI tools
  - Machine learning
  - Reporting

---

## Exam Takeaway Summary
- Non-uniform data is unavoidable
- Data transformation fixes inconsistencies
- AWS Glue = serverless ETL engine
- DataBrew = no-code transformation tool
- Masking supports compliance
- Clean data enables reliable analytics
