# Introduction to AWS Identity and Access Management (IAM) — Exam Notes

## What Is IAM? (EXAM CRITICAL)
**AWS Identity and Access Management (IAM)** is a web service that allows you to:
- Manage **authentication** (who can sign in)
- Manage **authorization** (what actions they can perform)
- Control access to AWS resources **without sharing credentials**

IAM enables **granular, least-privilege access**.

---

## Key IAM Characteristics (MEMORIZE)
- IAM is **GLOBAL**
  - Not tied to any specific Region
- Integrated with **most AWS services by default**
- Supports:
  - Password policies
  - Multi-Factor Authentication (MFA)
  - Identity federation
- No additional cost

---

## IAM Core Concepts Overview
| Concept | Purpose |
|------|-------|
| IAM User | Represents a person or service |
| IAM Group | Collection of users |
| IAM Policy | Defines permissions |
| IAM Role | Used for temporary access (exam topic later) |

---

## IAM Users
- Represents:
  - A **person**
  - An **application/service**
- Defined **inside your AWS account**
- All activity is **billed to your account**
- **Best practice**:
  - One IAM user per person
  - Never share credentials

---

## IAM User Credentials
An IAM user can have:

### Console Access
- Username + password
- Used for AWS Management Console

### Programmatic Access
- Access key ID
- Secret access key
- Used for:
  - AWS CLI
  - AWS API

⚠️ IAM user credentials are **long-term (permanent)** until rotated.

---

## Why NOT Assign Permissions Directly to Users?
- Not scalable
- Hard to audit
- Difficult to manage at scale

➡️ **Use IAM Groups instead**

---

## IAM Groups (BEST PRACTICE)
- A **collection of IAM users**
- Permissions are assigned at the **group level**
- All users inherit group permissions

### Benefits
- Easier permission management
- Scales well
- Clear visibility of access by job role

---

## IAM Group Rules (EXAM FAVORITES)
- Groups can contain **many users**
- Users can belong to **multiple groups**
- Groups **cannot contain other groups**
- Groups **do not have credentials**

---

## Root User vs IAM Users (EXAM TRAP)
- Root user:
  - Full access by default
- IAM users:
  - **No permissions by default**
  - Must be explicitly granted access

---

## IAM Policies — EXAM CRITICAL
IAM policies define **permissions**.

- Policies are attached to:
  - Users
  - Groups
  - Roles
- Written in **JSON**
- AWS evaluates policies on every request

---

## IAM Policy Structure (MEMORIZE)
Every policy statement MUST include:

| Element | Required | Purpose |
|------|---------|--------|
| Effect | ✔ | Allow or Deny |
| Action | ✔ | What actions are allowed/denied |
| Resource | ✔ | Which resources are affected |

---

## IAM Policy Example — Admin Access
```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "*",
    "Resource": "*"
  }]
}
