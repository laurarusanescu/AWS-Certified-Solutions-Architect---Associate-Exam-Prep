# Storage Types on AWS — Exam Notes

## AWS Storage Categories (EXAM CRITICAL)
AWS storage services fall into **three main categories**:

1. **File Storage**
2. **Block Storage**
3. **Object Storage**

Choosing the correct type depends on:
- Access pattern
- Performance needs
- Scalability
- Application design

---

## File Storage

### What Is File Storage?
- Stores data in a **hierarchical structure**
  - Folders and subfolders
- Each file has:
  - File name
  - Size
  - Creation date
  - Path (e.g. `/app/images/cat.png`)

---

### Key Characteristics
- Centralized file access
- Shared by multiple hosts
- Supports:
  - File locking
  - Standard file system protocols

---

### Common Use Cases
- Shared content repositories
- Development environments
- User home directories

---

### Traditional Equivalent
- **NAS (Network Attached Storage)**

---

## Block Storage

### What Is Block Storage?
- Data is split into **fixed-size blocks**
- Each block:
  - Has its own address
  - Contains no metadata
- Files are reconstructed from blocks on access

---

### Key Characteristics (EXAM FAVORITE)
- Very **low latency**
- High performance
- Efficient for frequent updates
- Only the changed block is updated

---

### Common Use Cases
- Databases
- Enterprise applications
- ERP systems
- Boot volumes

---

### Traditional Equivalent
- **DAS (Direct-Attached Storage)**
- **SAN (Storage Area Network)**

---

## Object Storage

### What Is Object Storage?
- Stores data as **objects**
- Objects are stored in a **flat structure**
- Each object includes:
  - Data
  - Unique identifier
  - Metadata

---

### Key Characteristics (EXAM CRITICAL)
- Highly scalable
- No hierarchy (no folders)
- Updating data requires replacing the whole object
- Designed for durability, not low latency

---

### Common Use Cases
- Media files (images, videos)
- Static assets
- Backups
- Large unstructured datasets

---

### Traditional Equivalent
- No direct traditional equivalent
- Cloud-native storage model

---

## File vs Block vs Object (EXAM COMPARISON)

| Feature | File | Block | Object |
|------|------|-------|--------|
| Structure | Hierarchical | Blocks | Flat |
| Metadata | File-level | None | Rich metadata |
| Performance | Medium | High | Lower |
| Scalability | Limited | Limited | Virtually unlimited |
| Best For | Shared files | Databases | Static & unstructured data |

---

## Cloud vs On-Prem Storage (EXAM INSIGHT)
- On-prem storage:
  - Requires purchasing hardware
  - Slow to scale
- Cloud storage:
  - Created in minutes
  - Elastic and scalable
  - No hardware management

---

## Exam Takeaway Summary
- File storage = shared file systems
- Block storage = high-performance, low latency
- Object storage = scalable, durable, unstructured
- Always match **storage type to workload**
