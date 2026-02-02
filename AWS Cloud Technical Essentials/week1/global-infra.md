# AWS Global Infrastructure — Exam-Focused Notes

## Data Durability & Redundancy
- Storing data locally (e.g., on a laptop) is **not durable**
- Cloud storage allows:
  - Data safety
  - Access from anywhere
- AWS stores data in **data centers** with built-in redundancy

---

## Data Centers
- Physical buildings that host servers
- Designed with:
  - Redundant power
  - Networking
  - Connectivity
- Not exposed directly to customers

---

## Availability Zones (AZs) — EXAM CRITICAL
- An **Availability Zone** is:
  - One or more data centers
  - Designed for **fault isolation**
- AZs are connected by:
  - **High-speed**
  - **Low-latency**
  - **Redundant links**
- Best practice:
  - Deploy workloads across **multiple AZs**

---

## Regions — EXAM CRITICAL
- A **Region** is a **geographic area**
- Contains **multiple Availability Zones**
- AZs inside a region are isolated but connected
- You **choose the Region** where your resources run

### Naming Example
- Regions are named by location  
  - Example: `us-east-1` (Northern Virginia)

---

## Region Selection Criteria (MEMORIZE)
When choosing an AWS Region, consider **FOUR factors**:

### 1. Compliance (MOST IMPORTANT)
- Legal or regulatory requirements
- Example:
  - Data must stay in the UK → use **London Region**
- If compliance applies:
  - **Other factors do not matter**

### 2. Latency
- Distance between users and AWS resources
- Closer region = lower latency
- Important for:
  - Web apps
  - User-facing applications

### 3. Pricing
- AWS pricing **varies by region**
- Differences due to:
  - Taxes
  - Operating costs
- Some regions are more expensive than others

### 4. Service Availability
- Not all AWS services are available in all regions
- New services often launch in limited regions first
- Must verify service support before choosing a region

---

## Global Infrastructure Hierarchy (EXAM FAVORITE)
- **Data Centers** → inside **Availability Zones**
- **Availability Zones** → inside **Regions**
- Designed for **high availability and fault tolerance**

---

## AWS Global Edge Network
- Used to reduce **latency**
- Consists of:
  - **Edge Locations**
  - **Regional Edge Caches**

---

## Edge Locations
- Used to cache content **closer to end users**
- Reduce latency for global users
- Common use case:
  - Websites
  - Static content
  - Media files

---

## Amazon CloudFront — EXAM SERVICE
- AWS **Content Delivery Network (CDN)**
- Uses **Edge Locations**
- Benefits:
  - Faster content delivery
  - Reduced latency
  - Improved user experience

---

## Key Exam Takeaways
- AZ ≠ Region
- Always design for **multiple AZs**
- Region choice = compliance → latency → price → services
- Edge locations ≠ Regions
- CloudFront uses **Edge Locations**, not AZs
