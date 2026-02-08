# Data Management Best Practices in Data Lakes — Notes

---

## Raw Data as the Source of Truth
- Best practice is to **ingest raw data in its original format**
- Raw data is:
  - Immutable
  - Auditable
  - The original source of truth
- Raw data is **not ideal for querying**
  - High compute cost
  - Poor performance

➡️ Raw data is often stored in **low-cost archival storage**
➡️ **Amazon S3 Glacier** is a good option for raw data retention

---

## Why Data Optimization Matters
- Cloud uses a **pay-as-you-go** model
- Inefficient data layouts cause:
  - More data scanned
  - Slower queries
  - Higher costs
- Optimized data:
  - Improves performance
  - Reduces query cost
  - Scales efficiently

---

## Four Core Data Management Best Practices (EXAM FAVORITE)

1. **Formatting**
2. **Partitioning**
3. **Compression**
4. **Compaction**

---

## 1. Data Formatting (EXAM CRITICAL)

### What Is Formatting?
- Choosing the **optimal file format** for analytics
- Strongly impacts:
  - Disk I/O
  - Query speed
  - Cost

---

### Row-Based Formats
Examples:
- CSV
- JSON

**Characteristics:**
- Data stored row by row
- Queries must scan every row

➡️ Inefficient for analytical workloads

---

### Columnar Formats (BEST PRACTICE)
Examples:
- **Apache Parquet**
- **Apache ORC**

**Characteristics:**
- Data stored column by column
- Only required columns are read

---

### Why Columnar Formats Are Faster
- Fewer disk I/O operations
- Faster query execution
- Lower compute usage
- Lower cost

---

### Example
Query:
sql
SELECT user_id FROM table;

# Data Optimization & Management in Data Lakes — Exam Notes

---

## Columnar vs Row-Based Formats (EXAM CRITICAL)

### CSV (Row-Based)
- Scans **every row and every column**
- Inefficient for analytics queries

### Parquet / ORC (Columnar)
- Reads **only required columns** (e.g., `user_id`)
- Drastically reduces disk I/O

➡️ **Massive performance improvement**

---

## AWS Support for Formatting
- **AWS Glue ETL jobs** can:
  - Convert **CSV / JSON → Parquet or ORC**
- No custom formatting logic required

---

## 2. Data Partitioning (EXAM CRITICAL)

### What Is Partitioning?
- Splitting data into **chunks you are likely to query**

### Common Partition Keys
- Date (`year / month / day`)
- Region
- Customer ID

---

### Why Partitioning Improves Performance
- Reduces data scanned
- Queries read **only relevant partitions**
- Lowers query cost

---

### Example
Taxi dataset partitioned by date:
text
s3://data-lake/taxi/year=2024/month=02/day=05/


# Data Optimization, Compaction & Security — Exam Notes

---

## Partitioning Example (RECAP)

### Querying February 5
- Reads **only that partition folder**
- Skips all other data

➡️ Dramatically reduces data scanned and query cost

---

## Partitioning Rule of Thumb
> Partition data by **how it is most frequently queried**

⚠️ Over-partitioning leads to:
- Too many small files
- Performance degradation  
(see **Compaction**)

---

## 3. Data Compression (EXAM FAVORITE)

### What Is Compression?
- Reducing file size using **compression algorithms**

---

### Common Compression Algorithms
- **Snappy**
- **GZIP**
- **LZO**

---

### Benefits of Compression
- Less storage used
- Less data scanned
- Faster queries
- Lower monthly cost

➡️ **Columnar formats + compression = best results**

---

## 4. Data Compaction (IMPORTANT CONCEPT)

### What Is Compaction?
- Combining **many small files** into **fewer larger files**

---

### Why Compaction Is Necessary
Too many small files cause:
- Excessive Amazon S3 API calls
- Slower query performance
- High metadata overhead

---

### Examples

**Bad**
- One file per hour
- One file per event

**Good**
- One file per day
- One file per logical batch

---

### AWS Support for Compaction
- **AWS Glue jobs** can:
  - Merge small files
  - Produce optimal file sizes

---

## Coffee Grinding Analogy (Mental Model)
- Espresso → very fine grind
- French press → coarse grind

➡️ Data layout should match **query patterns**  
➡️ File size = **“grind size”**

---

## Security Best Practices (JOB ZERO)

### Encryption in Transit
- Enabled by default in Amazon S3
- Uses **HTTPS / TLS**

---

### Encryption at Rest
- **Server-side encryption**
- **Client-side encryption**

➡️ Protects sensitive data in the data lake

---

## Typical Optimized Data Flow

1. Ingest raw data (CSV / JSON)
2. Store raw data (Amazon S3 / Glacier)
3. Use AWS Glue to:
   - Convert to Parquet / ORC
   - Partition data
   - Compress files
   - Compact small files
4. Query using **Amazon Athena**
5. Visualize using **Amazon QuickSight**

---

## Exam Takeaway Summary
- Raw data = source of truth
- Do **not** query raw data directly
- Columnar formats outperform row-based formats
- Partition by common query fields
- Compression reduces cost
- Compaction avoids small-file problems
- **AWS Glue automates optimization**
