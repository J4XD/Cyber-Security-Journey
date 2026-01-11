# 🔒 Day 4: File Permissions & CHMOD

**Date:** 10 Jan 2026

Today, I learned about Linux File Permissions. This is the core security feature of Linux. It decides "Who can do what" with a file. If permissions are weak, anyone can steal data!

### 📜 Understanding `rwx`

Every file has 3 types of permissions. I can see them by typing `ls -l`.
1. **r (Read) - Value 4:** Permission to open and read the file.
2. **w (Write) - Value 2:** Permission to edit or delete the file.
3. **x (Execute) - Value 1:** Permission to run the file (used for scripts/programs).

### 🔢 The Magic Numbers (CHMOD)
We use the `chmod` (Change Mode) command to set these permissions using math (4+2+1).

| Command | Math | Meaning |
| :--- | :--- | :--- |
| `chmod 777 file.txt` | 4+2+1 | **DANGER:** Everyone can read, write, and run this file. (Never use on servers). |
| `chmod 700 file.txt` | 4+2+1 (User only) | **Secure:** Only I can access this file. No one else. |
| `chmod +x script.py` | Add Executable | Makes a script runnable so I can use it as a tool. |

### 💻 My Practice:
I checked file permissions using `ls -l` and tried changing them:
1. Created a script: `touch virus.py`
2. Checked permissions: `ls -l virus.py` (It was not green/executable).
3. Made it executable: `chmod +x virus.py`
4. Checked again: `ls -l virus.py` (Now it's green and ready to run!)
