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
