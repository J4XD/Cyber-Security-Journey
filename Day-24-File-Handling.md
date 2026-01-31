# 📂 Day 24: File Handling (Reading Wordlists)

**Date:** 30 Jan 2026

Today, I learned how to read and write files using Python. This is essential for handling **Wordlists** (dictionaries of passwords/usernames) and saving scan results.

### 🔓 The `open()` Function
Python uses `open()` to interact with files. It takes two arguments: `Filename` and `Mode`.

| Mode | Meaning | Use Case |
| :---: | :--- | :--- |
| **"r"** | **Read** | Reading a password list. (Error if file doesn't exist). |
| **"w"** | **Write** | Creating a new report. (Overwrites existing content). |
| **"a"** | **Append** | Adding new logs to an old file. (Does not delete old data). |

---

### 🧠 The Best Way: `with open(...)`
In older Python versions, we had to manually close files using `file.close()`. If the code crashed, the file remained open (corrupted).
Now, we use the `with` keyword. It automatically closes the file, even if errors occur.

**Syntax:**
```python
with open("passwords.txt", "r") as file:
    content = file.read()
    print(content)
```
🧪 Hands-on Lab: Reading a Wordlist
I created a dummy password list and wrote a script to read it line by line.

Step 1: Create a Dummy Wordlist
Create a file named wordlist.txt in the same folder and add some text:
```Plaintext
admin
123456
password
iloveyou
root
```
Step 2: The Reader Script (read_files.py)
```python
print("--- WORDLIST READER ---")

filename = "wordlist.txt"

try:
    # Open the file in 'Read' mode
    with open(filename, "r") as f:
        
        # Read line by line
        for line in f:
            # .strip() removes the invisible "Enter" key (\n) at the end
            password = line.strip()
            
            print(f"Testing Password: {password}")
            
            # Here we can add logic: 
            # if password == "123456": login(password)

except FileNotFoundError:
    print("❌ Error: File not found! Please create 'wordlist.txt' first.")
```
Step 3: Writing Results (Logging)
I also learned how to save data.
```python
result = "Found Admin Password: 123456"

# 'a' mode appends data to the end
with open("scan_results.txt", "a") as log_file:
    log_file.write(result + "\n")

print("✅ Log saved to scan_results.txt")
```
📝 Hacker's Note
strip() is crucial: When Python reads a line, it also reads the "New Line" character (\n). If my password is admin, Python reads admin\n. This will cause login failure. Using .strip() cleans it to just admin.
