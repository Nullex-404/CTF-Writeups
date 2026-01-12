# 🧠 CTF Writeup – SQL Injection Login Bypass

## 📌 Challenge Overview

This challenge focuses on exploiting a vulnerable login page using **SQL Injection (SQLi)**.

The goal of the challenge is to:

- Analyze how the login system works
    
- Identify an SQL Injection vulnerability
    
- Exploit it to bypass authentication
    
- Retrieve the flag or gain access
    

This challenge simulates a **real-world web vulnerability** commonly found in poorly secured applications.

---

## 🛠 Technologies Involved

- Web application (login page)
    
- Backend database (SQL-based)
    
- User input fields:
    
    - Username
        
    - Password
        

---

## 🔍 Understanding the Login Logic

Most login systems follow this logic:

1. User submits a username and password
    
2. The application checks the database
    
3. If both values match a stored record → login succeeds
    
4. Otherwise → login fails
    

Behind the scenes, the application runs an **SQL query** to verify credentials.

---

## 🧪 Vulnerable SQL Query (Conceptual)

The backend executes a query similar to:

`SELECT * FROM users WHERE username = 'USER_INPUT' AND password = 'PASSWORD_INPUT';`

⚠️ **Problem:**  
User input is inserted **directly** into the SQL query **without validation or sanitization**.

This is the root cause of the vulnerability.

---

## 🚨 What Makes This Vulnerable?

SQL is a **logic-based language**.

If attackers can inject SQL logic into input fields, they can:

- Change conditions
    
- Bypass checks
    
- Force the query to always return `TRUE`
    

The database cannot tell the difference between:

- Trusted SQL code
    
- Malicious user input
    

---

## 💥 Exploiting the Vulnerability (SQL Injection)

Instead of entering a normal username, we inject SQL logic.

### Payload Used

`' OR '1'='1`

### Why This Works

- `'1'='1` is **always TRUE**
    
- `OR TRUE` overrides the password check
    
- The database returns the first user in the table
    
- Authentication is bypassed
    

---

## 🧠 Logical Breakdown

Original intent:

- username must match
    
- password must match
    

Injected logic:

- username matches **OR** a condition that is always true
    

Result:

- The WHERE clause becomes **true regardless of credentials**
    

---

## ✅ Outcome

- Login bypassed successfully
    
- Application grants unauthorized access
    
- Flag is revealed / protected page is accessed
    

This confirms the presence of an **SQL Injection vulnerability**.

---

## 🏴 Flag

`echo "czBtM19TUUxfODU4MzIyNzU=" > base64 | base64 -d `
