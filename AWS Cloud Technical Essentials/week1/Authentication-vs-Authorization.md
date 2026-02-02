# Protect the AWS Root User — Exam-Focused Notes

## Authentication vs Authorization (EXAM DEFINITIONS)

### Authentication
- Verifies **who you are**
- Answers: **“Are you who you say you are?”**
- Examples:
  - Username + password
  - Access keys
  - MFA codes
  - Biometrics

---

### Authorization
- Determines **what actions you can perform**
- Answers: **“What are you allowed to do?”**
- Implemented using:
  - IAM policies
  - Permissions

---

## AWS Root User — EXAM CRITICAL
- The **first identity** created when opening an AWS account
- Has **full, unrestricted access** to:
  - All AWS services
  - All resources
  - Billing and account settings
- Accessed using:
  - Email address + password used to create the account

---

## AWS Root User Credentials

### 1. Console Credentials
- Email address
- Password
- Used to access the **AWS Management Console**

### 2. Access Keys (PROGRAMMATIC ACCESS)
- Used for:
  - AWS CLI
  - AWS API
- Consist of:
  - **Access key ID**
  - **Secret access key**
- Must be protected like a password

---

## Root User Best Practices (MEMORIZE)
- 🔒 Use a **strong password**
- ❌ **Never share** root credentials
- ❌ **Do NOT use root user for daily tasks**
- ❌ **Delete or disable root access keys**
- ✅ Use root user **only when absolutely required**
- ✅ Lock away root credentials securely

---

## Root User Access Keys — EXAM RULE
- **Do NOT create root access keys**
- If they exist:
  - **Delete them immediately**
- Root access keys are a **major security risk**

---

## Multi-Factor Authentication (MFA) — EXAM FAVORITE

### Why MFA Matters
- Passwords can be:
  - Guessed
  - Cracked
  - Phished
- MFA adds an **extra layer of protection**
- Strongly recommended for:
  - **AWS root user**

---

## MFA Authentication Factors
MFA uses **two or more** of the following:

1. **Something you know**
   - Password
   - PIN
2. **Something you have**
   - MFA device
   - One-time passcode
3. **Something you are**
   - Fingerprint
   - Face scan

---

## MFA for AWS Root User
- Requires:
  - Email + password
  - Temporary numeric code from MFA device
- Best practice:
  - **Always enable MFA on the root user**

---

## Supported MFA Devices on AWS

### Virtual MFA
- Software apps
- Less secure than hardware
- Examples:
  - Google Authenticator
  - Microsoft Authenticator
  - Authy
  - Duo Mobile

---

### Hardware MFA
- Physical devices
- Generate one-time codes
- Examples:
  - Key fobs
  - Display cards

---

### U2F Security Keys
- Hardware device plugged into USB
- Very strong security
- Example:
  - YubiKey

---

## Exam Takeaway Summary
- Authentication = who you are
- Authorization = what you can do
- Root user = full access → **protect it**
- Never use root for daily work
- Delete root access keys
- **Enable MFA on root user — ALWAYS**
