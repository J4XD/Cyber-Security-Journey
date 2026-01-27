# 🔌 Day 21: Python Sockets (Network Communication)

**Date:** 27 Jan 2026

Today, I learned about the `socket` library. This is the foundation of all network hacking tools (Port Scanners, Reverse Shells, Keyloggers).
A **Socket** is simply an endpoint for communication. It allows my Python script to talk to another computer over the internet.

### 🧠 The Socket Recipe
To create a connection, we need two things:
1.  **IP Address** (The House Address)
2.  **Port Number** (The Door Number)

**Equation:** `IP + Port = Socket`

### 🛠️ Key Functions in `socket` Module

| Function | Description |
| :--- | :--- |
| `socket.socket()` | Creates a new socket object (Buys a new phone). |
| `connect((ip, port))` | Tries to connect to a target (Dials the number). |
| `send()` | Sends data to the target (Speaks). |
| `recv()` | Receives data from the target (Listens). |
| `close()` | Closes the connection (Hangs up). |

---

### 🧪 Hands-on Lab: Connecting to Google
I wrote a script to check if I can connect to Google's Web Server (Port 80).

**Script:** `test_connection.py`
```python
import socket
import sys

# 1. Create a Socket Object
# AF_INET = IPv4
# SOCK_STREAM = TCP
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

target_ip = "8.8.8.8" # Google DNS (or use 'google.com')
port = 53 # DNS Port (Usually Open)

print(f"Connecting to {target_ip} on port {port}...")

# 2. Try to Connect
try:
    # We pass a 'tuple' (ip, port)
    s.connect((target_ip, port))
    print(f"✅ Connection Successful! Port {port} is OPEN.")

except Exception as e:
    print(f"❌ Connection Failed: {e}")

# 3. Always Close the socket
finally:
    s.close()
```
🛡️ Why use try-except? (Error Handling)
In networking, things fail all the time (Target offline, Firewall blocks, etc.). If we don't use try-except, our tool will crash with an ugly error message. As a hacker, I want my tool to say "Port Closed" gracefully, not crash.

📝 Hacker's Perspective
This simple script is actually a Single Port Scanner. If connect() succeeds -> Port is OPEN. If connect() fails -> Port is CLOSED. Tomorrow, I will put this in a loop to build a full Port Scanner!
