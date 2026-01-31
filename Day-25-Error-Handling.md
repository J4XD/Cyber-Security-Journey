# 🛑 Day 25: Error Handling (Making Tools Robust)

**Date:** 31 Jan 2026

Today, I learned how to handle errors gracefully using `try` and `except`.
A professional tool should never show raw Python errors (Tracebacks) to the user. It should catch the error and show a helpful message.

### 🧠 The Structure
It works like a safety net.
* **Try:** "Koshish karo ye code chalane ki."
* **Except:** "Agar koi gadbad ho, toh crash mat hona, ye wala code chalana."
* **Finally:** "Error ho ya na ho, ye kaam zarur karna (jaise connection close karna)."

### 🚦 Common Hacker Errors

| Exception Name | Meaning | Use Case |
| :--- | :--- | :--- |
| **KeyboardInterrupt** | User pressed `Ctrl + C`. | Stopping a scan midway without ugliness. |
| **socket.gaierror** | Hostname not found. | When user enters a wrong URL/IP. |
| **socket.timeout** | Connection took too long. | Handling slow servers. |
| **FileNotFoundError** | File doesn't exist. | When Wordlist is missing. |
| **ValueError** | Wrong data type. | User entered "abc" instead of Port "80". |

---

### 🧪 Hands-on Lab: The Crash-Proof Script
I wrote a script that intentionally breaks but handles it like a pro.

**Script:** `safe_input.py`
```python
import sys

print("--- ROBUST INPUT SYSTEM ---")

while True:
    try:
        # 1. Ask for Port Number
        port_input = input("\nEnter Target Port (1-65535) or 'q' to quit: ")

        # Check for quit
        if port_input.lower() == 'q':
            print("Exiting...")
            break

        # 2. Try to convert string to integer (This can crash if user types text)
        port = int(port_input)

        # 3. Validate Logic
        if 1 <= port <= 65535:
            print(f"✅ Scanning Port {port}...")
            # (Here we would put our socket code)
        else:
            print("⚠️ Invalid Port! Must be between 1-65535.")

    except ValueError:
        # This runs if user types "hello" instead of a number
        print("❌ Error: Please enter a NUMBER, not text!")

    except KeyboardInterrupt:
        # This runs if user presses Ctrl+C
        print("\n\n🚫 Scan aborted by user (Ctrl+C). Exiting gracefully.")
        sys.exit()

    except Exception as e:
        # This catches any other unknown error
        print(f"❌ Unexpected Error: {e}")
```
📝 Hacker's Perspective
When I run a Brute Force attack, it might take hours.

If I press Ctrl+C to stop it, I don't want the data I found to be lost.

Using a try-except block, I can save the results to a file before the script exits.

Example Snippet:
```python
try:
    start_attack()
except KeyboardInterrupt:
    print("\nSaving results before quitting...")
    save_log()
    sys.exit()
```
🛠️ Homework: Improve Old Tools
Do you remember the scanner.py we built on Day 22?
It had a major flaw: If you pressed Ctrl + C to stop the scan mid-way, it crashed with a long, ugly error message (Traceback).

Task: Open your scanner.py file and wrap your main code inside a try-except block to handle this gracefully.
```python
import sys
import socket

try:
    # Paste your old scanner code here (the logic loop)
    # ...
    
except KeyboardInterrupt:
    print("\n\n🚫 Program stopped by User.")
    sys.exit()

except socket.gaierror:
    print("\n❌ Hostname could not be resolved.")
    sys.exit()

except socket.error:
    print("\n❌ Server not responding.")
    sys.exit()
```
Next Up: Tomorrow, we will build Phase 3's Second Project—"The Password Cracker". 🔐
We will attempt to crack a Zip file or a Login password using Python (utilizing Wordlists and File Handling). 🚀
