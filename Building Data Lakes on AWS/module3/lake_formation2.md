# AWS Lake Formation Basics — Notes

---

## What Is AWS Lake Formation? (EXAM CRITICAL)
**AWS Lake Formation** helps you:
- Centrally **govern**
- **Secure**
- **Share**
- **Manage**

data in a data lake for **analytics and machine learning**.

It works with:
- **Amazon S3** (data storage)
- **AWS Glue Data Catalog** (metadata)

---

## Core Purpose of Lake Formation
- Breaks down **data silos**
- Combines **structured and unstructured data**
- Enables **secure self-service analytics**
- Reduces operational complexity

---

## Typical Lake Formation Workflow
1. Identify existing data stores  
   - Amazon S3  
   - Relational databases  
   - NoSQL databases  
2. Move data into the data lake (S3)
3. Crawl and catalog data (Glue Crawlers)
4. Prepare data for analytics
5. Provide secure access to analytics services

---

## Fine-Grained Access Control (EXAM FAVORITE)

### Lake Formation Permissions Model
- Lake Formation provides its **own permissions model**
- Augments (does not replace) **IAM**
- Uses a **grant / revoke** model (similar to RDBMS)

---

### Granularity of Permissions
Permissions can be applied at:
- Database level
- Table level
- **Column level**
- **Row level**
- **Cell level**

➡️ Much more granular than IAM alone

---

## Services Enforced by Lake Formation
Permissions apply across:
- Amazon Athena
- Amazon QuickSight
- Amazon Redshift Spectrum
- Amazon EMR
- AWS Glue

---

## Hybrid Access Mode (EXAM CONCEPT)

### What Is Hybrid Access Mode?
- Uses **both**:
  - Lake Formation permissions
  - IAM permissions
- Allows **incremental onboarding**

### Why It Matters
- Migrate gradually
- Secure one use case at a time
- Avoid disruptive permission changes

---

## Cross-Account Data Sharing (EXAM FAVORITE)
Lake Formation enables sharing:
- Across AWS accounts
- Across AWS Organizations
- Directly with IAM principals in other accounts

Includes:
- Glue Data Catalog metadata
- Underlying S3 data
- Fine-grained permissions

---

## Lake Formation Permissions Management Flow

### High-Level Steps
1. **Define Policies**
   - Admin sets table policies (allow/deny)
2. **Grant Permissions**
   - Grant access on databases/tables
   - Register S3 locations with Lake Formation
3. **Get Metadata**
   - User submits query (Athena, Glue, EMR, Redshift Spectrum)
   - Engine requests metadata from Glue Data Catalog
4. **Check Permissions**
   - Glue checks with Lake Formation
   - Returns only authorized metadata
5. **Get Credentials (Credential Vending)**
   - Lake Formation issues temporary credentials
6. **Get Data**
   - Engine accesses S3
   - Applies column/row/cell filtering
   - Returns results to user

---

## If a Table Is NOT Managed by Lake Formation
- Engine accesses S3 directly
- Permissions evaluated using:
  - IAM policies
  - S3 bucket policies

---

## Security Best Practices
- Follow **IAM best practices**
- Prefer Lake Formation for centralized governance
- Use encryption:
  - At rest (AWS KMS)
  - In transit (TLS/SSL)

---

## Key Advantages of Lake Formation
- Centralized governance
- Fine-grained access control
- Secure self-service analytics
- Cross-account sharing
- Reduced operational overhead
- Native integration with AWS analytics services

---

## Exam Takeaway Summary
- Lake Formation governs data lakes on S3
- Glue Data Catalog stores metadata
- Fine-grained permissions (column/row/cell)
- Hybrid mode = gradual adoption
- Credential vending = temporary secure access
