# 🧠 Day 17: Python Logic (If, Else & Conditions)

**Date:** 23 Jan 2026

Today, I learned how to make my Python scripts "smart" using **Conditional Statements**.
In hacking, we use this logic everywhere. For example: "If the port is open, attack it. If not, skip it."

### 🚦 The Logic Flow
Python uses English-like keywords:
* **if:** Agar ye sach hai, toh ye karo.
* **elif:** (Else If) Agar upar wala galat hai, toh ye check karo.
* **else:** Agar kuch bhi sach nahi hai, toh ye karo.

> **⚠️ Critical Rule: Indentation**
> Python doesn't use `{}` like Java or C++. It uses **Spaces (Tabs)**.
> Lines inside an `if` block MUST be shifted to the right.

---

### 🧪 Hands-on Lab: Writing a Security Script
I wrote a simple script that acts like a "Login System".

**Step 1: Open Terminal & Create File**
```bash
nano login.py
```
Step 2: Write the Code
```bash
print("--- SECURE LOGIN SYSTEM ---")

username = input("Enter Username: ")
password = input("Enter Password: ")

# Check credentials
if username == "admin" and password == "secret123":
    print("✅ Access Granted! Welcome, Admin.")
    print("Starting security scan...")

elif username == "guest":
    print("⚠️ Access Restricted. You can only view public files.")

else:
    print("❌ Access Denied! Incorrect username or password.")
    print("Alert: Intruder detected!")
```
Step 3: Run the Script
```bash
python3 login.py
```

I tried entering wrong passwords to see the "Access Denied" message.

### ⚙️ Comparison Operators (The Tools)
To make decisions, we need to compare things. Here is the cheat sheet:

| Operator | Meaning | Example |
| :---: | :--- | :--- |
| `==` | **Equals** (Check if same) | `if ip == "192.168.1.1":` |
| `!=` | **Not Equals** | `if user != "root":` |
| `>` | **Greater Than** | `if port > 1000:` |
| `<` | **Less Than** | `if ping < 50:` |
| `and` | **Both** must be true | `if user == "admin" and pass == "123":` |
| `or` | **At least one** is true | `if port == 80 or port == 443:` |

📝 Hacker's Perspective
When writing Malware or Exploits, we check for Environment. For example, some attacks only work if we are Root.
```bash
import os

# Check if user is Root (ID is always 0)
if os.geteuid() != 0:
    print("Error: You must run this script as ROOT!")
    exit()
else:
    print("Hacking started...")
```
