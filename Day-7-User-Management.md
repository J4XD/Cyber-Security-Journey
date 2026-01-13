# 👑 Day 7: Users & Privileges (Root Power)

**Date:** 13 Jan 2026

Today, I learned about User Management in Linux. Unlike Windows personal PCs, Linux is designed to handle multiple users at once. Security is all about permissions—keeping normal users away from system files.

### 🧠 Key Concepts:
1.  **Root (Superuser):** The administrator account with unlimited power. It can delete anything (even the OS itself).
2.  **Standard User:** A normal account with limited access. Cannot install software or change system settings without permission.
3.  **Sudo (SuperUser DO):** A magic command that allows a standard user to run specific commands with Root privileges temporarily.

### 🛠️ Commands I Learned:

| Command | Usage | Description |
| :--- | :--- | :--- |
| `whoami` | Check Identity | Tells me which user I am currently logged in as. |
| `sudo <cmd>` | Run as Root | Runs a command with administrative power (asks for password). |
| `useradd <name>` | Create User | Creates a new user account (Requires sudo/root). |
| `passwd <name>` | Set Password | Sets or changes the password for a user. |
| `su <name>` | Switch User | Switches from the current user to another user. |
| `deluser <name>` | Delete User | Removes a user from the system. |

### 🧪 Hands-on Lab: Creating a New Identity
I practiced creating a new user and switching to it.

**Step 1: Check who I am**
```bash
whoami
# Output: root (or your username)

Step 2: Create a new user named "hacker"
Step 3: Set a password for the new user

Bash

passwd hacker

Step 4: Switch to the new user

Bash

su hacker
Now, when I type whoami, it says "hacker". I have successfully changed my identity!

Step 5: Return to original user

Bash

exit
# (I typed a new password when prompted)

