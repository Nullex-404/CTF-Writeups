# SQL Injection – Login Bypass (CTF)
## Description

- This writeup demonstrates a classic SQL Injection vulnerability
	in a login page challenge, solved in a legal CTF environment.

- The goal was to analyze the authentication logic and gain access
	to the admin account in order to retrieve the flag.
## What is SQL Injection (Reference)

- SQL Injection (SQLi) is a critical web vulnerability listed by OWASP.
	It occurs when user input is improperly handled and directly included
	in SQL queries, allowing attackers to manipulate query logic.
## Login Logic Explanation

- The application uses an SQL query to authenticate users by checking
	the username and password against records stored in the database.

- If both values match, access is granted.
## Observation

- Submitting crafted input caused the application to crash,
	which indicates improper input handling and potential SQL Injection.
## Analysis

- By manipulating the login logic using a logical condition that always
	evaluates to true, the authentication check was bypassed.

- This works because the backend query does not properly validate
	or sanitize user input.
## Result

- Authentication was successfully bypassed,
	and the admin account was accessed.

- **The flag was retrieved.**
## Disclaimer
- This writeup is for educational purposes only.
	All testing was performed in a legal CTF environment.
	Do not attempt these techniques on real systems without authorization.
