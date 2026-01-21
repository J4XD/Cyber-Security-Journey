# 🚪 Day 15: TCP, UDP & Common Ports

**Date:** 21 Jan 2026

**Phase 2 Finale:** Today, I learned how computers talk to specific applications using **Protocols** and **Ports**. This is the final piece of the Networking puzzle.

### 📞 TCP vs. UDP (The Two Ways to Talk)

Data travels in packets. But how are these packets sent?

#### 1. TCP (Transmission Control Protocol) - "The Reliable Guy"
* **Nature:** Connection-Oriented.
* **How it works:** It establishes a connection first ("Handshake") before sending data.
    * *Step 1:* "Hello, are you there?" (SYN)
    * *Step 2:* "Yes, I am here." (SYN-ACK)
    * *Step 3:* "Okay, sending data now." (ACK)
* **Pros:** **Reliable**. No data is lost. If a packet drops, it resends it.
* **Use Case:** Websites (HTTP), Emails, File Transfers. (Where accuracy matters).

#### 2. UDP (User Datagram Protocol) - "The Fast Guy"
* **Nature:** Connection-Less.
* **How it works:** It just throws data at the target. It doesn't care if it reaches or not. "Fire and Forget".
* **Pros:** **Extremely Fast**. No waiting for acknowledgments.
* **Use Case:** Streaming (YouTube), Online Gaming, Video Calls. (If a frame drops, the video just glitches for a millisecond, it doesn't stop).

---

### 🔢 Common Ports (The Room Numbers)
Every service on a server runs on a specific "Port Number" (0-65535). As a hacker, I scan these ports to see what is running.

| Port | Service | Protocol | Why Hackers Love It? |
| :--- | :--- | :--- | :--- |
| **21** | FTP | TCP | File Transfer. Often misconfigured allowing anonymous login. |
| **22** | **SSH** | TCP | Secure Login. If I crack this password, I own the server. |
| **23** | Telnet | TCP | Old insecure login. Sends passwords in clear text! |
| **53** | DNS | UDP | Converts Names to IPs. Target for Spoofing attacks. |
| **80** | **HTTP** | TCP | Web Server (Unsecured). I can sniff traffic here. |
| **443** | **HTTPS** | TCP | Secure Web Server. Harder to sniff (Encrypted). |
| **3389** | RDP | TCP | Windows Remote Desktop. Famous target for Ransomware. |

---

### 🧪 Hands-on Lab: Listening to Ports
I checked which "Doors" (Ports) are open on my own machine.

**Command:**
```bash
sudo netstat -tuln
```
-t: TCP ports

-u: UDP ports

-l: Listening (Open) ports

-n: Show numbers (not names)

Output Observation: I saw 0.0.0.0:80 -> This means my computer is running a Web Server!
