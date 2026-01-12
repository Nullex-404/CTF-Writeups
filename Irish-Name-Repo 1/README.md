# SQL Injection – Login Bypass

**Category:** Web / Pentesting  
**Type:** SQL Injection (Authentication Bypass)

---

## Description

A vulnerable login page that directly uses user input in SQL queries.  
The goal is to bypass authentication and access the admin account.

---

## Vulnerability

- Unsanitized user input
- Dynamic SQL query
- No prepared statements

---

## Exploit Payload

```sql
' OR 1=1--