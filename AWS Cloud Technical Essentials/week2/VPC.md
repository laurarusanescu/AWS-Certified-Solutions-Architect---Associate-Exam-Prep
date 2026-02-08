# Amazon VPC & Networking — Exam Notes

## What Is a VPC? (EXAM CRITICAL)
A **Virtual Private Cloud (VPC)** is a **logically isolated network** in AWS, similar to an on-premises data center network.

---

## VPC Creation — Required Choices
When creating a VPC, you must define:

1. **VPC name**
2. **Region**
   - A VPC spans **multiple Availability Zones** within one Region
3. **IP range (CIDR block)**
   - Example: `10.0.0.0/16`
   - Each VPC can have **up to 4 /16 CIDR blocks**

➡️ CIDR block determines network size

---

## Subnets (EXAM CRITICAL)

### What Is a Subnet?
- A **subnet** is a smaller network inside a VPC
- Comparable to VLANs in on-prem networks
- Used in AWS for:
  - High availability
  - Connectivity control

---

### Subnet Creation — Required Choices
When creating a subnet, choose:

1. VPC
2. Availability Zone (AZ)
3. Subnet CIDR (must be a subset of VPC CIDR)
   - Example:
     - VPC: `10.0.0.0/16`
     - Subnet: `10.0.0.0/24`

➡️ EC2 instances are launched **inside subnets**

---

## High Availability in a VPC (EXAM GOLD)
- Subnets are **AZ-specific**
- Best practice:
  - Create **at least 2 subnets**
  - Place them in **different AZs**
- Design for failure:
  - If one AZ fails, others remain available

---

## Reserved IP Addresses (EXAM DETAIL)
AWS reserves **5 IP addresses per subnet** for:
- Network address
- VPC router
- DNS
- Future use
- Broadcast (unused but reserved)

### Example
- Subnet `/24` = 256 IPs
- Usable IPs = **251**

➡️ Common design:
- VPC `/16`
- Subnets `/24`

---

## Gateways

### Internet Gateway (IGW) — EXAM CRITICAL
- Enables **internet access** for a VPC
- Must be:
  - Created
  - **Attached to the VPC**
- Highly available and scalable

➡️ Required for public subnets

---

### Virtual Private Gateway (VGW)
- Connects VPC to **another private network**
- Used with:
  - Customer Gateway (on-prem side)
- Enables:
  - Encrypted **VPN connections**

---

## Route Tables (EXAM CRITICAL)

### Main Route Table
- Automatically created with the VPC
- Controls routing for subnets by default
- Default rule:
  - Allows traffic between all subnets in the VPC

---

### Route Table Components
- **Destination**:
  - IP range for traffic
- **Target**:
  - Where traffic is sent (IGW, VGW, local)

---

### Custom Route Tables
- Used for **granular routing control**
- Can be associated with specific subnets
- If associated:
  - Subnet uses it **instead of** main route table
- Always includes local VPC route by default

---

## Network Access Control Lists (NACLs)

### What Is a NACL?
- Subnet-level firewall
- Controls inbound and outbound traffic

---

### NACL Characteristics (EXAM FAVORITE)
- **Stateless**
  - Must allow both inbound AND outbound traffic
- Rules are evaluated in **numerical order**
- Explicit **DENY** at the end

---

### Default NACL
- Allows:
  - All inbound traffic
  - All outbound traffic

---

### Example NACL Rule Logic
- Allow inbound HTTPS (443)
- Allow outbound ephemeral ports (1025–65535)

➡️ Required because NACLs are stateless

---

## Security Groups (EXAM CRITICAL)

### What Is a Security Group?
- Instance-level firewall
- Attached to **EC2 instances**

---

### Security Group Characteristics
- **Stateful**
  - Response traffic is automatically allowed
- Default behavior:
  - ❌ All inbound blocked
  - ✅ All outbound allowed

---

### Common Web Server Rules
- Allow inbound:
  - HTTP (80)
  - HTTPS (443)
- Source:
  - `0.0.0.0/0`

---

## Security Groups vs NACLs (EXAM TRAP)

| Feature | Security Group | NACL |
|------|---------------|------|
| Scope | Instance | Subnet |
| Stateful | ✅ Yes | ❌ No |
| Default | Deny inbound | Allow all |
| Rule Order | All evaluated | Numbered order |

---

## Multi-Tier Architecture with Security Groups
- Web tier:
  - Internet → HTTPS
- App tier:
  - Web tier → HTTP
- Database tier:
  - App tier → MySQL

➡️ Isolation via **security groups**, not VLANs

---

## Public EC2 Troubleshooting Checklist (EXAM FAVORITE)

1. **Internet Gateway**
   - IGW attached to VPC

2. **Route Table**
   - `0.0.0.0/0` → IGW

3. **Security Group**
   - Inbound HTTP/HTTPS allowed

4. **NACL**
   - Inbound + outbound rules allowed

5. **Public IP**
   - EC2 has a public IP assigned

6. **Protocol**
   - HTTP vs HTTPS mismatch

7. **User Data**
   - Script executed successfully

8. **IAM Permissions**
   - Instance role allows required service access

9. **Local Network**
   - No firewall/proxy blocking access

10. **Application**
   - Web server running
   - App deployed correctly

---

## Exam Takeaway Summary
- VPC = isolated network
- Subnets = AZ-scoped
- IGW = internet access
- Route tables control traffic flow
- NACLs = stateless subnet firewall
- Security groups = stateful instance firewall
- HA = multiple AZs
