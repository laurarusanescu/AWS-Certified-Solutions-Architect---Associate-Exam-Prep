# Week 2 Customer Call — Requirements & Current State (Clickstream Analytics)

---

## Customer & Product Context
- Customer is a **software company** providing **restaurant menus via QR codes**
- Current core product:
  - **Amazon S3 Static Website Hosting** serves an **HTML menu page**
  - Restaurant admins can **update menu objects** in S3 (prices, descriptions, images, etc.)
  - Company generates **QR codes** that point to the menu page (1 QR code per table)

---

## New Feature They Want
### “Order this item” Upgrade (Context Only)
- They want to add an option on the menu page to **call an existing API** to place orders
- **Payment processing is handled by a third-party payment service**
- This feature is **not the focus** of the analytics architecture (just context)

---

## Main Goal for This Week: Clickstream Analytics
They want analytics to help restaurants optimize menus, such as:
- Which dishes are viewed most
- Whether users scroll through the full menu or stop early (apps vs entrees, etc.)
- Drop-off points (viewed description but not added to tab)
- Time between expanding an item and purchasing
- Behavior insights for reporting and optimization (BI-style insights)

➡️ This is **clickstream data analysis**

---

## What They Already Have (IN SCOPE SUPPORTING CONTEXT)
- A **JavaScript library** that collects clickstream events on the client
- They only need a backend endpoint to **receive** the events

---

## Key In-Scope Requirements (What We Must Deliver)

### 1) Data Ingestion Endpoint (EXAM CRITICAL)
- Provide a **RESTful HTTPS endpoint**
- Client will send events via **HTTP POST**
- Must support “REST standards” (their preference)

---

### 2) Serverless + Managed Services (HIGH PRIORITY)
- They operate with a **reduced staff**
- Prefer **managed / serverless** services
- Want to avoid:
  - EC2 instances
  - OS maintenance
  - Manual operations

---

### 3) Cost Optimization (EXAM FAVORITE)
- Cost is a priority
- Prefer services that bill by **actual usage** (pay-per-request / pay-per-GB)
- Avoid “always-on” cost models where possible

---

### 4) Durability + Cross-Region Backup
- Ingested data must be stored durably
- They want a **backup copy in another AWS Region**

---

### 5) Security Requirements (JOB ZERO)
- **Encryption in transit** (HTTPS/TLS)
- **Encryption at rest**
- Secure-by-default expectations

---

## Explicit Scope Clarification (IMPORTANT)
### Out of Scope
- Client-side clickstream code (already done)
- Payment gateway integration
- Restaurant ordering API details (already exists)

### In Scope
- Data ingestion + storage + processing + analytics + visualization architecture
- Meeting requirements: **serverless, low-cost, durable, secure, cross-region backup**

---

## Early Architecture Signals (Where This Is Heading)
Based on requirements, a likely direction includes:
- **API Gateway** as HTTPS REST endpoint (managed)
- **Serverless ingestion pipeline**
- Durable storage in **Amazon S3**
- **Cross-region replication/backup** strategy
- Analytics stack for querying + dashboards (Athena/QuickSight-style pattern)

---

## Exam Takeaway Summary
- Clickstream = event data about user behavior
- Start with clear **in-scope vs out-of-scope**
- Prefer **managed + serverless** for low ops
- Pay-per-use services fit spiky workloads
- Plan for **cross-region durability**
- Encrypt **in transit + at rest**
