# Role-Based Access in AWS — IAM Best Practices (Exam Notes)

## Lock Down the AWS Root User (EXAM CRITICAL)
- Root user has **full, unrestricted access**
- If compromised → total account takeover

### Best Practices
- ❌ Never share root credentials
- ❌ Delete root access keys (if they exist)
- ✅ Enable **MFA** on the root user
- ✅ Use root **only when absolutely required**

---

## Principle of Least Privilege (EXAM GOLD)
- Grant **only the minimum permissions required**
- Start with:
  - No permissions
  - Add permissions **incrementally**
- Applies to:
  - Users
  - Groups
  - Roles

---

## Use IAM Appropriately (COMMON TRAP)
IAM is used for:
- Managing access to AWS resources
- Creating users, groups, and roles **inside one AWS account**

IAM is **NOT** used for:
- Website user authentication (sign-up / sign-in)
- Protecting operating systems
- Network-level security

---

## Use IAM Roles When Possible (VERY IMPORTANT)

### IAM Roles
- Do **not** have long-term credentials
- Provide **temporary credentials**
- Credentials:
  - Automatically expire
  - Valid for **15 minutes to 36 hours**

### IAM Users
- Have **long-term credentials**
- Require manual rotation

### Exam Rule
➡️ **Prefer IAM roles over IAM users**

---

## Why IAM Roles Are Better
- More secure (temporary credentials)
- Easier to manage
- Ideal for:
  - AWS services accessing other AWS services
  - Cross-account access
  - Federated users

---

## Identity Providers (IdP)
- Used to manage identities **outside AWS**
- Examples:
  - Corporate directories
  - Third-party IdPs
  - AWS-managed IdP

### Benefits
- Centralized identity management
- No need to create IAM users in each account
- Use **IAM roles** for access

---

## AWS IAM Identity Center (Successor to AWS SSO)

### What It Is
- An **identity provider** for AWS
- Allows:
  - Single sign-on (SSO)
  - One set of credentials
  - Access to multiple AWS accounts

---

### Key Advantages (EXAM RELEVANT)
- Central user and group management
- Supports third-party IdP integration
- Syncs users and groups automatically
- Separates:
  - Identity management (IdP)
  - Cloud access management (AWS)

---

## When to Use IAM Identity Center
- Multiple AWS accounts
- Many employees
- Need centralized access control
- Want SSO across AWS accounts and apps

---

## Exam Takeaway Summary
- Root user → lock it down
- Least privilege → always
- IAM ≠ website authentication
- Prefer **IAM roles** over users
- Use **IdP + roles** for scale
- IAM Identity Center = centralized SSO
