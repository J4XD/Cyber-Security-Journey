# 🔎 Day 5: Finding Data with Grep & Pipes

**Date:** 11 Jan 2026

Today, I learned how to search for specific text inside huge files. As a hacker, I will often need to find specific information (like passwords, errors, or flags) inside large log files without reading them line by line.

### 🛠️ The Tools:

| Symbol/Command | Name | Usage |
| :--- | :--- | :--- |
| `grep "text"` | Search | Finds and prints lines matching the text. |
| `|` | Pipe | Takes the output of the first command and gives it to the next command. |
| `head` | Head | Shows only the first 10 lines of a file. |
| `tail` | Tail | Shows only the last 10 lines of a file. |

### ⚡ Practical Examples:

**1. Using Grep alone:**
If I want to find the word "Error" inside a file named `server.log`:
`grep "Error" server.log`

**2. The Power of Piping (`|`):**
Combining commands makes them powerful.
`cat huge_wordlist.txt | grep "password123"`
*(This reads the file and immediately filters out only the line containing "password123")*

### 🧪 Hands-on Lab: Try it yourself
I practiced this by creating a fake "secret" file. You can try this too:

**Step 1: Create a file with some data**
```bash
echo "This is just random text" > server_data.txt
echo "user: admin" >> server_data.txt
echo "pass: super_secret_123" >> server_data.txt
