# 📡 Day 9: Linux Networking Basics

**Date:** 15 Jan 2026

Today, I learned the fundamental networking commands in Linux. Before attacking any system, a hacker must know their own IP address and check if the target system is reachable.

### 🧠 Key Concepts:
1.  **IP Address:** The digital address of my computer (e.g., `192.168.1.5`).
2.  **Ping:** A tool to check if another computer or website is online (like poking someone to see if they react).
3.  **Localhost:** My own computer (Address is always `127.0.0.1`).

### 🛠️ Commands I Learned:

| Command | Usage | Description |
| :--- | :--- | :--- |
| `ip a` | Check IP | Shows all IP addresses assigned to my network interfaces. (New version of `ifconfig`). |
| `ifconfig` | Check IP | The classic command to see network configuration (Might need installation). |
| `ping <url>` | Check Connection | Sends data packets to a target to see if it replies. |
| `wget <link>` | Download File | Downloads a file from the internet directly to the terminal. |
| `curl <link>` | Read Web Page | Fetches the content of a webpage (HTML) without opening a browser. |

### 🧪 Hands-on Lab: Network Recon
I practiced finding my IP and checking connectivity.

**Step 1: Finding my IP Address**
I used the `ip` command to see my network details.
```bash
ip a
```
**Step 2: Checking Internet Connectivity (Ping) I checked if I could reach Google's server.**
```bash
ping google.com
```
**Step 3: Downloading a File (wget) I downloaded a test image from the web.**
```bash
wget https://github.com/github.png
```
**Output: The file 'github.png' was saved in my folder.**
