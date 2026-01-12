# ⚙️ Day 6: Process Management (The Task Manager)

**Date:** 12 Jan 2026

Today, I learned how to manage running programs (processes) in Linux. In Windows, we use "Task Manager" to close frozen apps. In Linux, we use the terminal to find and kill processes.

### 🧠 Key Concepts:
1.  **Process:** Any running program is called a process.
2.  **PID (Process ID):** Every process has a unique number (like an ID card). We need this ID to control the process.

### 🛠️ Commands I Learned:

| Command | Usage | Description |
| :--- | :--- | :--- |
| `top` | Real-time View | Shows all running processes like Task Manager (Press `q` to exit). |
| `ps` | Process Status | Shows a snapshot of current processes. |
| `ps aux` | Detailed View | Shows ALL processes running on the system (even background ones). |
| `kill <PID>` | Stop Process | Asks the process to stop gracefully. |
| `kill -9 <PID>` | **Force Kill** | Instantly destroys the process (The Nuclear Option ☢️). |

### 🧪 Hands-on Lab: Creating & Killing a Dummy Process
I practiced how to find a PID and kill a specific task using a safe command called `sleep`.

**Step 1: Create a dummy process**
I ran a command that sleeps for 1000 seconds in the background (`&` runs it in background).
```bash
sleep 1000 &
