# CodeAlpha_Secure_Coding_Review
# Task 3: Secure Coding Review (Code Audit Report)

## 1. Project Overview
This report documents the security code review performed on a Python-based web application component. The objective of this audit is to identify potential security vulnerabilities via manual inspection and provide remediation steps to secure the codebase.

---

## 2. Vulnerability 1: SQL Injection (SQLi)

### 🔴 Vulnerable Code Snippet
Insecure implementation using direct string formatting for database queries:

```python
import sqlite3

def get_user_data(username):
    conn = sqlite3.connect('users.db')
    cursor = conn.cursor()
    
    # CRITICAL VULNERABILITY: String concatenation allows SQL Injection
    query = f"SELECT * FROM users WHERE username = '{username}'"
    cursor.execute(query)
    
    return cursor.fetchall()
