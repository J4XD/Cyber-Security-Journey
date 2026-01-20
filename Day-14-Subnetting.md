# ✂️ Day 14: Subnetting & CIDR (The Network Math)

**Date:** 20 Jan 2026

Today, I tackled the "Math" of Networking: **Subnetting**.
Simply put, Subnetting is the process of cutting a large network into smaller, manageable pieces (Sub-networks).

### 🧠 The Core Concept: Network ID vs. Host ID
Every IP address has two parts. Imagine an address like **"123, MG Road"**.
1.  **Network ID (MG Road):** The name of the street. Everyone on this street shares this part.
2.  **Host ID (123):** The specific house number. This is unique for everyone on that street.

**Who decides where the Street Name ends and House Number starts?**
👉 The **Subnet Mask**.

---

### 🎭 The Subnet Mask
You have seen this number before: `255.255.255.0`.
It acts like a filter.
* **255** means: "This part belongs to the Network (Street)."
* **0** means: "This part is for the User (House)."

**Example:**
IP: `192.168.1.10`
Mask: `255.255.255.0`
* **Network ID:** `192.168.1` (The Street)
* **Host ID:** `.10` (The House)

---

### 📏 CIDR Notation (The Slash `/`)
Hackers don't like writing long numbers like `255.255.255.0`. We use short-code called **CIDR** (Classless Inter-Domain Routing).
You will often see IPs written like: **`192.168.1.5/24`**

**What does `/24` mean?**
It means the first **24 bits** (8+8+8) are "ON" (Network part).
* 8 bits = 255.
* So `/24` is just a short way of writing `255.255.255.0`.

| CIDR | Subnet Mask | Total IPs | Use Case |
| :--- | :--- | :--- | :--- |
| **/8** | 255.0.0.0 | 16 Million | Huge ISPs / Countries |
| **/16** | 255.255.0.0 | 65,536 | Large Offices |
| **/24** | 255.255.255.0 | 256 | **Home WiFi / Small Labs** |

---

### 🧮 The Magic Number: 256
In a standard Home Network (`/24`), we have **256** total spots (0 to 255).
But we can only use **254**. Why?
1.  **Network Address (.0):** Represents the whole group (Start).
2.  **Broadcast Address (.255):** Used to shout to everyone (End).
3.  **Usable IPs:** .1 to .254 (Where our devices live).

### ⚔️ Hacker's Perspective (Why do I need this?)
When I want to hack a WiFi network, I need to scan **all** connected devices.
I won't scan the whole internet. I will tell my tool (Nmap) to scan only the Subnet.
* **Command:** `nmap 192.168.1.0/24`
* This tells Nmap: *"Scan from 192.168.1.0 to 192.168.1.255. Don't go outside this street."*

### 📝 Homework
1.  Check your IP again using `ip a`.
2.  Look for the `/` number next to your IP (e.g., `192.168.29.45/24`).
3.  If it says `/24`, it means you can have up to 254 devices in your house network.
