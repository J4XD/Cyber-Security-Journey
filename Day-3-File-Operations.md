# 📄 Day 3: Managing Files (Action Mode)

**Date:** 09 Jan 2026

Today, I moved beyond just navigating folders. I learned how to create, read, copy, move, and delete files using the command line. This is where the real work happens.

### 🛠️ Key Commands I Learned:

| Command | Action | Example Code |
| :--- | :--- | :--- |
| `touch` | Creates a new empty file instantly. | `touch secret.txt` |
| `cat` | Reads/Displays file content on the screen. | `cat secret.txt` |
| `cp` | Copies a file (Backup). | `cp secret.txt copy_secret.txt` |
| `mv` | Moves a file OR Renames it. | `mv secret.txt hidden.txt` |
| `rm` | **Deletes** a file permanently. | `rm useless_file.txt` |

### ⚠️ Important Lesson:
I learned that the `rm` command is dangerous. Unlike Windows, Linux **does not have a Recycle Bin** for the terminal. If I delete a file using `rm`, it is gone forever. I need to be careful!

### 💻 Practice (Hands-on):
I tried this sequence in the terminal:
1. Created a file: `touch hacker.txt`
2. Renamed it: `mv hacker.txt pro_hacker.txt`
3. Deleted it: `rm pro_hacker.txt` (Cleared my tracks!)
