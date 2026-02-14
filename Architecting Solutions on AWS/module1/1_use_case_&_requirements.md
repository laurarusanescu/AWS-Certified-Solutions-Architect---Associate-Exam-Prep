# Customer Use Case — Migrating an Orders Service to AWS (Notes)

---

## Customer Background
- Company: **Any Company Ecommerce**
- Business:
  - Sells cleaning products globally
  - Public website + mobile app for customers
  - Separate wholesale website for buyers
- Architecture status:
  - Many services already migrated to AWS (mostly lift-and-shift)
  - **Orders service** still hosted on-premises
  - Opportunity to **rewrite this service cloud-natively**

---

## Current Orders Service (On-Premises)
- Single backend service that:
  - Validates and authenticates orders
  - Stores orders in a **MySQL database**
  - Calls downstream services:
    - Inventory fulfillment
    - Accounting
- Web server and application run on the **same server**
- Payment processing handled by an **external payment gateway**

---

## Problems with the Current Architecture (EXAM FAVORITE)

### 1. Scaling Issues
- Demand is **spiky**
  - Huge traffic during sales or coupon campaigns
  - Near-zero traffic at other times
- On-premises hardware requires **overprovisioning**
- Cannot scale quickly enough → slow or failed orders

---

### 2. Tight Coupling
- Business logic tightly coupled in a single service
- Downstream calls are sequential and dependent
- If the application crashes mid-process:
  - Some downstream services may be updated
  - Others are not
- Results in **data inconsistency** and customer issues

---

### 3. Operational Overhead
- Managing a MySQL database for a **single table**
- High effort for:
  - Maintenance
  - Availability
  - Durability
- Customer wants a **more hands-off database solution**

---

## Customer Goals for the Migration

### Primary Goals
- Move orders service to AWS
- Rewrite service using **cloud-native architecture**
- Reduce operational overhead
- Improve resilience and reliability

---

### Key Requirements
- **Automatic scaling**
  - Scale up during traffic spikes
  - Scale down when demand is low
- **Decoupled architecture**
  - Downstream services should operate independently
- **High availability and durability**
- **Cost optimization**
- **Performance optimization**
- **Easy monitoring and logging**
  - Unified logging system across components

---

## Database Requirements
- Open to changing databases
- Needs:
  - High availability
  - High durability
  - Minimal management effort
- Preference for a **managed, serverless-friendly database**

---

## Architectural Direction (Initial Signals)
From the discussion, the ideal solution likely includes:
- **Serverless backend**
- **Event-driven architecture**
- **Managed AWS services**
- **Loose coupling between components**

---

## Key Architecture Challenges to Solve
- Handle spiky traffic automatically
- Prevent cascading failures
- Ensure downstream calls are reliable
- Maintain data consistency
- Minimize operational burden
- Optimize cost under variable demand

---

## Exam Takeaway Summary
- Lift-and-shift ≠ cloud-native
- Spiky workloads benefit from serverless
- Tight coupling reduces resilience
- Decoupling improves fault tolerance
- Managed services reduce ops overhead
- Monitoring and logging should be centralized
