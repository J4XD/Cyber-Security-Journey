# 📦 Day 23: Python Libraries (pip & requests)

**Date:** 29 Jan 2026

Today, I learned how to install external libraries to make Python even more powerful. I also explored the `requests` library, which allows my script to browse the internet just like Chrome/Firefox.

### 📥 What is PIP?
* **Full Form:** Pip Installs Packages.
* **Concept:** It is the "App Store" for Python. If I need a tool for hacking, data science, or web dev, I can just type `pip install <name>`.

**Command I ran:**
```bash
pip install requests
```
(This installed the 'requests' library from the internet).

🌐 The 'Requests' Module (Web Hacking Base)
The requests library lets Python send HTTP packets to websites. This is how we build tools for:

Directory Busting (Finding hidden /admin pages).

Brute Forcing (Trying passwords on login pages).

SQL Injection (Sending malicious inputs).

🧪 Hands-on Lab: Analyzing a Website Headers
I wrote a script to fetch the "Hidden Information" (Headers) that websites send back.

Script: web_header_grabber.py
```python
import requests
import sys

# 1. Take URL from user
if len(sys.argv) < 2:
    print("Usage: python3 web_header_grabber.py <url>")
    sys.exit()

url = sys.argv[1]

print(f"🕵️ Scanning Headers for: {url}")

try:
    # 2. Send a GET request (Like opening the site in browser)
    response = requests.get(url)

    # 3. Check Status Code (200 = OK, 404 = Not Found)
    print(f"Status Code: {response.status_code}")

    # 4. Print Server Headers (Hidden Info)
    # This often reveals the Server Software (Apache/Nginx) and OS!
    print("\n[+] Server Headers:")
    for key, value in response.headers.items():
        print(f"  {key}: {value}")

except Exception as e:
    print(f"❌ Error: {e}")
```
🏃‍♂️ Running the Script
```bash
python3 web_header_grabber.py [https://www.google.com](https://www.google.com)
```
What I noticed:
I saw headers like Server, Date, and Content-Type. Hackers use this to identify what technology the website is using (Reconnaissance).

### 🚦 HTTP Status Codes (Cheat Sheet)
When using `requests`, the most important thing is the status code.

| Code | Meaning | Hacker Interpretation |
| :---: | :--- | :--- |
| **200** | **OK** | ✅ Page exists! (Target found) |
| **404** | **Not Found** | ❌ Page doesn't exist. |
| **403** | **Forbidden** | 🔒 Page exists but I am blocked (Permission Denied). |
| **302** | **Redirect** | ↩️ Moved to another page (Often happens after login). |
| **500** | **Server Error** | 💥 Server crashed! (Potential for Bug Bounty). |
