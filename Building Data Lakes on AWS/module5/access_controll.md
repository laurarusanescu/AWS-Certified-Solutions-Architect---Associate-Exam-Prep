
# AWS Lake Formation Permissions & Access Control — Notes

---

## Why Access Control Matters in a Data Lake
A data lake without access control can quickly become a security risk.

Key concern:
- **Who is allowed to access which data?**

➡️ AWS Lake Formation provides **fine-grained access control**, so you are not limited to “all or nothing” permissions.

---

## Fine-Grained Access Control (EXAM CRITICAL)
With Lake Formation, you can control access at multiple levels:
- **Row-level**
- **Column-level**
- **Row + column combinations**
- **Cell-level** (most granular)

➡️ Different users can see different parts of the same dataset.

---

## Example Use Case: Marketing vs Finance
- Dataset contains:
  - Sales data
  - Customer financial information
- **Marketing team**:
  - Needs access to sales performance
  - Does NOT need customer financial data
- **Finance team**:
  - Needs access to sensitive financial details

➡️ Lake Formation allows:
- Marketing → limited rows/columns
- Finance → full access

---

## How Lake Formation Permission Enforcement Works (EXAM FAVORITE)

### Step-by-Step Flow
1. **User requests data**
2. Lake Formation checks permissions
3. If authorized:
   - Lake Formation issues **temporary credentials**
4. Another AWS service (e.g., Athena) uses those credentials
5. Data is fetched from **Amazon S3**
6. Filtering is applied (row/column/cell)
7. Results are returned to the user

➡️ This process is seamless to the end user  
➡️ Called **credential vending**

---

## Granularity of Permissions
Lake Formation supports:
- Database-level permissions
- Table-level permissions
- Column-level permissions
- Row-level permissions
- Cell-level permissions

➡️ Extremely precise control over data access

---

## Scaling Permissions with Lake Formation Tags (EXAM CONCEPT)

### What Are Lake Formation Tags?
- **Key–value pairs**
- Similar to AWS resource tags

Examples:
- `environment = dev | qa | prod`
- `classification = confidential`
- `department = finance`

---

### Where Tags Can Be Applied
- Databases
- Tables
- Columns
- Any combination of the above

---

### Tag-Based Permissions
- Permissions can be granted based on tags
- Example:
  - Dev IAM group → access to all resources tagged `environment=dev`

➡️ Makes permissions:
- Easier to manage
- Easier to update
- More scalable

---

## Cross-Account Data Access
Lake Formation supports:
- Sharing data across AWS accounts
- Centralized control from a primary data lake account
- Granting access to external accounts

➡️ Ideal for multi-account data lake architectures

---

## Recommended Lake Formation Roles (BEST PRACTICE)

### IAM Administrator
- Manages IAM users, roles, and policies
- Full IAM control

---

### Data Lake Administrator
- Full control of data lake resources
- Manages:
  - Databases
  - Tables
  - Permissions
- Acts as the **“lifeguard”** of the data lake

---

### Data Engineers
- Build and maintain pipelines
- Run ETL jobs
- Higher level of access than analysts

---

### Data Analysts
- **Read-only access**
- Query and analyze data
- No modification privileges

---

### Workflow Role
- Assumed by AWS services
- Allows services (Glue, Athena, etc.) to:
  - Access data lake
  - Process data on behalf of users

---

## Key Advantages of Lake Formation Permissions
- Fine-grained control
- Secure by default
- Scales with data growth
- Easy to manage with tags
- Works across AWS analytics services

---

## Exam Takeaway Summary
- Lake Formation controls who can “swim” in the data lake
- Permissions can be row, column, or cell-level
- Uses temporary credentials (credential vending)
- Tags simplify permission management
- Supports cross-account access
- Clear role separation improves governance
