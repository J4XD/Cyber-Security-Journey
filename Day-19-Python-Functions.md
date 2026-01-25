# 🧩 Day 19: Python Functions (Organizing Code)

**Date:** 25 Jan 2026

Today, I learned about **Functions**. A Function is a block of code that only runs when it is called. It helps me avoid writing the same code again and again.
Think of it like a **Tool**: You don't build a screwdriver every time you need it; you just pick it up and use it.

### 🧠 Syntax: The 'def' Keyword
To create a function, we use `def` (define).

```python
# 1. Define the Function (Making the Tool)
def attack_target():
    print("🚀 Launching Attack...")
    print("💥 Target Down!")

# 2. Call the Function (Using the Tool)
attack_target()
attack_target() # I can use it as many times as I want!
```
📥 Arguments & Parameters (Passing Data)
Real tools need inputs (like a specific IP to scan). We pass these inputs inside the ().

Example: A Custom Scanner Function
```python
def scan_port(ip, port):
    print(f"🔍 Scanning IP: {ip} on Port: {port}")
    
    if port == 80:
        print("✅ HTTP Service Found (Web Server)")
    elif port == 22:
        print("✅ SSH Service Found (Secure Login)")
    else:
        print("❌ Port Closed")

# Calling the function with different data
scan_port("192.168.1.5", 80)
scan_port("10.0.0.1", 22)
```
📤 Return Statement (Getting Results Back)
Sometimes, we don't want to just print; we want the answer back so we can use it later.
```python
def check_vulnerability(version):
    if version < 5.0:
        return "Critical Risk 🚨"
    else:
        return "Safe ✅"

# Store the result in a variable
status = check_vulnerability(4.2)
print(f"System Status: {status}")
```
🧪 Hands-on Lab: Building a Modular Tool
I created a script that uses functions to simulate a multi-step hacking process.

Script: hack_tool.py
```python
import time

# Function 1: Connect
def connect_to_server(ip):
    print(f"🔌 Connecting to {ip}...")
    time.sleep(1)
    return True

# Function 2: Brute Force
def crack_password(user):
    print(f"🔓 Cracking password for user: {user}...")
    time.sleep(1)
    return "secret123"

# Main Logic
target_ip = "192.168.1.100"

if connect_to_server(target_ip):
    print("Connection Successful!")
    password = crack_password("admin")
    print(f"🎉 Success! Password is: {password}")
```
