# Cyber-Security-Journey
My daily progress from Noob to Pro.

# My Cyber Security Journey 🚀

**Start Date:** 07 Jan 2026
**Status:** Beginner (Noob)

### 🎯 My Roadmap (From Basic to Advanced)

**Phase 1: Linux Mastery 🐧** (Current Focus)
- [ ] **Basic:** Navigation, File Management, CLI commands.
- [ ] **Advanced:** File Permissions, User Management (`sudo`), Bash Scripting.
- *Goal: Operate any Linux server comfortably using only the terminal.*

**Phase 2: Networking Deep Dive 🌐**
- [ ] **Basic:** IP, MAC, DNS, Ports & Protocols.
- [ ] **Advanced:** OSI Model, Subnetting, Packet Analysis (Wireshark), VPNs.
- *Goal: Understand exactly how data flows across the internet to find vulnerabilities.*

**Phase 3: Python for Security 🐍**
- [ ] **Basic:** Syntax, Loops, Functions, Error Handling.
- [ ] **Advanced:** Socket Programming, Writing custom tools (Port Scanners, Hash Crackers).
- *Goal: Stop using other people's tools and start building my own.*

**Phase 4: Web Hacking & CTFs 🚩**
- [ ] **Basic:** HTTP Basics, Google Dorking.
- [ ] **Advanced:** OWASP Top 10 (SQL Injection, XSS), Burp Suite, Metasploit.
- *Goal: legally hack and secure applications.*

### 📅 Day 1 Update:
Today, I set up my GitHub repository.
I learned that the **CIA Triad** is the foundation of information security:
- **C**onfidentiality (Keeping data secret)
- **I**ntegrity (Preventing unauthorized data alteration)
- **A**vailability (Ensuring data is always accessible)

# 🐧 Linux Basics - Day 2

**Date:** 08 Jan 2026

Today, I started learning the Linux Command Line Interface (CLI). Unlike Windows, where we mostly use a mouse, Linux relies heavily on terminal commands for efficiency and control.

### 📂 Essential Commands I Learned:

| Command | Full Form | Description |
| :--- | :--- | :--- |
| `pwd` | Print Working Directory | Tells me "Where am I?" in the file system. |
| `ls` | List | Shows all files and folders in the current location. |
| `mkdir <name>`| Make Directory | Creates a new folder (directory). |
| `cd <name>` | Change Directory | Moves me into a specific folder. |
| `cd ..` | Change Directory Back | Takes me one step back/up in the folder structure. |
| `clear` | Clear Screen | Cleans up the terminal window. |

### 🧠 Why is this important?
Most hacking tools and servers run on Linux. Mastering the terminal is the first step to becoming a security professional.
---
### 🛠️ How to Practice Online (No Installation Needed)

If you don't have a high-end PC or Linux installed yet, don't worry! You can practice these commands directly in your web browser.

**Resource:** [JSLinux by Fabrice Bellard](https://bellard.org/jslinux/)

**Steps to use:**
1. Open the link above.
2. Click on **"Alpine Linux"** (Console).
3. Wait for the black terminal screen to load.
4. Start typing commands like `ls`, `pwd`, or `mkdir hacker_folder` to practice!

**Note:** This runs safely inside your browser. No data is saved on your computer.

# 📄 Working with Files in Linux (Day 3)

**Date:** 09 Jan 2026

Today, I learned how to manage files using the Linux terminal. In Windows, we use a mouse to copy, paste, or delete files, but in Linux, we use commands for everything.

### 🛠️ Key Commands I Learned:

| Command | Action | Example Code |
| :--- | :--- | :--- |
| `touch` | Creates a new empty file instantly. | `touch secret.txt` |
| `cat` | displaying the file content on the screen. | `cat secret.txt` |
| `cp` | Copies a file (Backup). | `cp secret.txt copy_secret.txt` |
| `mv` | Moves a file OR Renames it. | `mv secret.txt hidden.txt` |
| `rm` | **Deletes** a file permanently. | `rm useless_file.txt` |

### ⚠️ Important Lesson:
I learned that the `rm` command is dangerous. Unlike Windows, Linux **does not have a Recycle Bin** for the terminal. If I delete a file using `rm`, it is gone forever. I need to be careful!

### 💻 Practice:
I tried these commands in an online terminal:
1. Created a file using `touch`.
2. Added some text and read it using `cat`.
3. Renamed the file using `mv`.
4. Deleted the file using `rm` to clear my tracks.
