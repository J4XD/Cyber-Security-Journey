# 🔄 Day 18: Python Loops (The Power of Automation)

**Date:** 24 Jan 2026

Today, I learned how to repeat tasks automatically using **Loops**.
In Hacking, we never do repetitive work manually. We write loops to scan networks, crack passwords, and flood servers.

### 🧠 The Two Types of Loops

| Loop Type | Concept | Hacker Use Case |
| :--- | :--- | :--- |
| **For Loop** | Runs for a **fixed** number of times. | "Scan IP addresses from 192.168.1.1 to 192.168.1.255" |
| **While Loop** | Runs **until** a condition becomes False. | "Keep trying passwords until access is granted." |

---

### 1️⃣ The For Loop (Range & Lists)
Used when we know *how many times* we want to run the code.

**Example 1: Scanning a Range of Ports**
```python
print("--- Starting Port Scan ---")

# Scan ports 1 to 10 (11 is excluded in range)
for port in range(1, 11):
    print(f"Scanning Port: {port}")

print("Scan Complete!")
```
Example 2: Scanning Specific Targets (List)
```bash
targets = ["192.168.1.5", "10.0.0.1", "172.16.0.5"]

for ip in targets:
    print(f"Attacking Target: {ip}")
```
2️⃣ The While Loop (The Stubborn Loop)
Used when we don't know when to stop. It keeps running as long as the condition is True.

Example: A Password Cracker Simulation
```bash
correct_password = "secret"
guess = ""

while guess != correct_password:
    guess = input("Enter Password to Crack: ")
    
    if guess == correct_password:
        print("✅ Access Granted!")
    else:
        print("❌ Wrong Password! Trying again...")
```
⚠️ Warning: Be careful with while True: (Infinite Loop). If you don't add a break command, it will run forever and crash your terminal! (Press Ctrl + C to force stop).

🧪 Hands-on Lab: Building a 'Brute Force' Simulator
I combined Lists and Loops to simulate a Brute Force Attack.

Script: brute_force.py
```bash
import time

# A list of common passwords (dictionary)
passwords = ["123456", "password", "admin", "secret123", "iloveyou"]
target_pass = "secret123"

print("--- STARTING BRUTE FORCE ATTACK ---")

for attempt in passwords:
    print(f"Trying password: {attempt}")
    time.sleep(0.5)  # Pause for 0.5 seconds to look cool
    
    if attempt == target_pass:
        print(f"🎉 PASSWORD CRACKED: {attempt}")
        break  # Stop the loop immediately
    else:
        print("❌ Failed.")

print("Attack Finished.")
```
