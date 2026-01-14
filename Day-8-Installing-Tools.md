# 📦 Day 8: Installing Software (APT & Git)

**Date:** 14 Jan 2026

Today, I learned how to install new programs and tools in Linux. Unlike Windows, where we download `.exe` files from websites, Linux uses a centralized "Package Manager" (like an App Store) to install software securely.

### 🧠 Key Concepts:
1.  **Repository:** A safe online storage where official Linux software is kept.
2.  **APT (Advanced Package Tool):** The command-line tool used to search, install, and update software from the repository.
3.  **Git:** A tool to download code directly from GitHub (used for many hacking scripts).

### 🛠️ Commands I Learned:

| Command | Usage | Description |
| :--- | :--- | :--- |
| `sudo apt update` | Refresh List | Checks for the latest version of available software (does not install anything). |
| `sudo apt upgrade` | Update All | Actually updates the installed software to the new versions. |
| `sudo apt install <name>` | Install App | Downloads and installs a specific package (e.g., `sudo apt install python3`). |
| `sudo apt remove <name>` | Uninstall | Removes a package from the system. |
| `git clone <url>` | Download Repo | Downloads a project/tool directly from GitHub. |

### 🧪 Hands-on Lab: Installing a System Info Tool
I practiced installing a cool tool called `neofetch` that displays system info in a graphical way.

**Step 1: Update the repository list**
Always update the list before installing anything.
```bash
sudo apt update
```
**Step 2: Install the tool I used apt to install Neofetch.**
```bash
sudo apt install neofetch
# (Type 'y' and Enter if asked to confirm)
```
**Step 3: Run the tool**
```bash
neofetch
```
Output: It showed a cool logo of my Linux OS along with RAM and CPU details.

**Step 4: Cloning a Tool from GitHub I also learned how to download tools that are not in the APT store using Git.**
```bash
git clone https://github.com/j4xd/Cyber-Security-Journey.git
```
# This downloaded my own repository to my local machine!
