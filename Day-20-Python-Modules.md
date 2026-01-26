# 📦 Day 20: Python Modules (The Hacker's Toolbox)

**Date:** 26 Jan 2026

Today, I learned about **Modules**. A Module is a file containing Python code (functions/variables) that I can include in my project.
Instead of writing complex code to interact with the Hard Disk or Network, I can just `import` it.

### 🔑 The 'import' Keyword
To bring a tool into my script, I use `import`.

```python
import os       # Operating System tools
import time     # Time & Sleep tools
import sys      # System specific parameters
```
🖥️ The 'os' Module (Controlling Linux)
This is the most used module in basic hacking scripts. It allows Python to execute Terminal Commands.

Example: Running a Ping Sweep
```python
import os

print("Pinging Google...")
# os.system runs the command just like I type in terminal
os.system("ping -c 3 google.com")
```
⌨️ The 'sys' Module (Command Line Arguments)
Professional tools (like Nmap) take inputs from the command line, not inside the code.

Bad Way: Edit code to change IP -> ip = "192.168.1.1"

Pro Way: Pass IP while running -> python3 tool.py 192.168.1.1

How sys.argv works: It creates a list of arguments.

sys.argv[0] = Script Name (tool.py)

sys.argv[1] = First Argument (The IP)

Example:
```python
import sys

# Check if user provided an IP
if len(sys.argv) < 2:
    print("Usage: python3 scanner.py <Target-IP>")
    exit()

target_ip = sys.argv[1]
print(f"Attacking Target: {target_ip}")
```
🧪 Hands-on Lab: Building a System Recon Tool
I created a script that gathers system information using the os module.

Script: recon.py
```python
import os
import platform
import datetime

print("--- SYSTEM RECONNAISSANCE TOOL ---")

# 1. Get OS Details
print(f"OS Platform: {platform.system()}")
print(f"OS Version: {platform.release()}")

# 2. Get Current Time
now = datetime.datetime.now()
print(f"Scan Time: {now}")

# 3. Check Who Am I (Running Linux Command)
print("\n[+] Current User Identity:")
os.system("whoami")

# 4. Check Network Config
print("\n[+] Network Configuration:")
os.system("ip a | grep inet") # Shows only IP lines
```
Running the script:
```python
python3 recon.py
```
