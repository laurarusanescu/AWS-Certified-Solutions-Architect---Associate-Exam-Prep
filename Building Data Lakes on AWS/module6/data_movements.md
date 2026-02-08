# Data Movement Scenarios in Modern Data Lakes — Notes

---

## Data Lake as the Center
In modern data architectures, the **data lake remains at the center**.

What changes is:
- **Direction of data flow**
- **Where data originates**
- **Where data is consumed**

Understanding data movement patterns helps:
- Optimize performance
- Reduce cost
- Choose the right AWS services

---

## Three Data Movement Models (EXAM CONCEPT)

1. **Inside-Out**
2. **Outside-In**
3. **Around the Perimeter**

---

## 1. Inside-Out Data Movement (EXAM FAVORITE)

### What Is Inside-Out?
- Data originates **inside the data lake**
- Data is shared **outward** to other services or consumers
- Data lake acts as the **single source of truth**

➡️ Key phrase: **single source of truth**

---

### Common Use Cases
- Sharing curated data with:
  - External partners
  - Customers
  - Regulatory bodies
- Moving processed data to:
  - Data warehouses
  - Reporting systems

---

### Example
- Raw data ingested into S3
- Transformed data stored in the lake
- A subset of data exported to:
  - Amazon Redshift for daily reporting

---

### Key Characteristics
- Data lake owns the authoritative dataset
- Other services consume derived data
- Strong governance is critical

---

## 2. Outside-In Data Movement (EXAM FAVORITE)

### What Is Outside-In?
- Data **primarily exists outside** the data lake
- Data is ingested **into the lake for processing**
- Data lake is used **on demand**

---

### Common Use Cases
- Ingesting third-party data:
  - Market data
  - Social media feeds
  - External datasets
- Enriching internal data with external sources

---

### Example
- Query results copied from operational databases
- Data loaded into the data lake
- ML models run using:
  - Amazon SageMaker
  - AWS Glue
  - Amazon EMR

---

### Key Characteristics
- Data lake is a **processing and analytics hub**
- Data may not be stored permanently
- Optimized for large-scale computation

---

## 3. Around-the-Perimeter Data Movement (EXAM CONCEPT)

### What Is Around-the-Perimeter?
- Data is **not centralized exclusively** in the data lake
- Services exchange data **directly with each other**
- Data lake participates **only when needed**

---

### Common Use Cases
- Offloading workloads between services
- Improving performance and scalability

---

### Example
- Copy data from a database to a search service
- Use Amazon OpenSearch for queries
- Avoid overloading the source database

➡️ Data moves **service-to-service**, not through the lake

---

### Key Characteristics
- Hybrid approach
- Reduced data movement
- Lower latency
- Services coexist as part of the data architecture

---

## Comparing the Three Models

| Model | Data Origin | Data Lake Role |
|-----|------------|---------------|
| Inside-Out | Data lake | Single source of truth |
| Outside-In | External systems | Processing & analytics |
| Around the Perimeter | Mixed | Optional participant |

---

## AWS Support for Data Movement
Regardless of the model, AWS provides services to support:
- Data ingestion
- Data sharing
- Data processing
- Data integration

➡️ The right service depends on **direction, scale, and purpose**.

---

## Exam Takeaway Summary
- Data lake stays central in all models
- Inside-Out = lake → services
- Outside-In = services → lake
- Around-the-Perimeter = service ↔ service
- Choose model based on data ownership and usage
