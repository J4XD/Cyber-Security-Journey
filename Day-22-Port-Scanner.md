# 🛠️ Day 22: Building a Python Port Scanner

**Date:** 28 Jan 2026

Today, I combined Loops, Logic, and Sockets to build my first real security tool: **A Port Scanner**.
This script will take an IP address, loop through a range of ports, and tell me which ones are open.

### 🧠 The Logic
1.  **Input:** Take the Target IP from the user.
2.  **Loop:** Run a `for` loop from Port 1 to 100 (or more).
3.  **Connect:** Try to make a socket connection to each port.
4.  **Check:**
    * If Connection == Success (0) -> **Port is OPEN**.
    * If Connection == Fail -> **Port is CLOSED**.
5.  **Timeout:** If a port doesn't answer in 1 second, move to the next (don't wait forever).

---

### 🧪 Hands-on Lab: The 'Mini-Nmap' Script
I wrote this script to scan my local network.

**Script:** `scanner.py`
```python
import sys
import socket
from datetime import datetime

# 1. Define the Target
# We take the IP from the command line (e.g., python3 scanner.py 192.168.1.1)
if len(sys.argv) == 2:
    target = socket.gethostbyname(sys.argv[1]) # Translate hostname to IP
else:
    print("Invalid amount of arguments.")
    print("Syntax: python3 scanner.py <ip>")
    sys.exit()

# 2. Add a Pretty Banner
print("-" * 50)
print(f"Scanning Target: {target}")
print(f"Time started: {str(datetime.now())}")
print("-" * 50)

try:
    # 3. The Scan Loop (Scanning ports 50 to 85)
    # You can change this range (e.g., 1, 1000)
    for port in range(50, 85):
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        socket.setdefaulttimeout(1) # Don't wait more than 1 second
        
        # connect_ex returns 0 if successful, error code if failed
        result = s.connect_ex((target, port)) 
        
        if result == 0:
            print(f"✅ Port {port} is OPEN")
        
        s.close() # Close connection before next loop

except KeyboardInterrupt:
    print("\nExiting program.")
    sys.exit()

except socket.gaierror:
    print("Hostname could not be resolved.")
    sys.exit()

except socket.error:
    print("Could not connect to server.")
    sys.exit()
```
🏃‍♂️ How I ran it:
I tested it on Google (Scanning limited ports is legal for educational purposes, but never scan unauthorized networks!).
```python
python3 scanner.py 8.8.8.8
```
Output:
```Plaintext
--------------------------------------------------
Scanning Target: 8.8.8.8
Time started: 2026-01-28 10:00:00
--------------------------------------------------
✅ Port 53 is OPEN
```
