# Explore Databases on AWS — Exam Notes

---

## Background: Enterprise Databases
- Historically, companies:
  - Chose **one database vendor**
  - Used it for **all applications**
- Since the 1970s, the dominant choice has been:
  - **Relational databases**

---

## What Is a Relational Database? (EXAM CRITICAL)
- Organizes data into **tables**
- Tables consist of:
  - **Rows** (records)
  - **Columns** (attributes)
- Tables can be **linked** using shared columns
  - This creates **relationships**

---

## Relational Schema (EXAM DETAIL)
- Structure defined by:
  - Tables
  - Columns
  - Relationships
- Known as a **logical schema**
- Schema is:
  - **Fixed**
  - Hard to change after deployment
- Requires **upfront data modeling**

---

## Relational Database Management System (RDBMS)
An **RDBMS** is software used to create and manage relational databases.

### Common RDBMS Examples
- MySQL
- PostgreSQL
- Oracle
- SQL Server
- Amazon Aurora

---

## SQL (Structured Query Language)
- Used to interact with RDBMS
- Example:
  ```sql
  SELECT * FROM table_name;
