# 🌐 Day 13: IP Addressing (The Identity on Internet)

**Date:** 19 Jan 2026

Today, I learned about **IP (Internet Protocol) Addresses**. While the MAC Address works inside my house (Local Network), the IP Address allows me to travel the world (Internet).

### 🧠 Concept: What is an IP Address?
* **Definition:** A unique string of numbers separated by periods (dots) that identifies each computer using the Internet Protocol.
* **IPv4 (Version 4):** The most common version. It looks like `192.168.1.1`.
    * It is **32-bit** long.
    * It has 4 parts (called Octets).
    * Each part ranges from **0 to 255**.

---

### 🏛️ The 5 Classes of IP (The Size Game)
Just like train compartments have classes, IPs have classes based on network size.

| Class | Range (1st Octet) | Use Case | Example |
| :--- | :--- | :--- | :--- |
| **Class A** | 1 - 126 | Huge Companies (Google, Apple) | `8.8.8.8` (Google DNS) |
| **Class B** | 128 - 191 | Medium Companies/Universities | `172.16.x.x` |
| **Class C** | 192 - 223 | **Home & Small Offices** (My Router) | `192.168.1.1` |
| **Class D** | 224 - 239 | Multicasting (Streaming) | Not used for PCs. |
| **Class E** | 240 - 255 | Research/Military | Reserved. |

*(Note: 127.0.0.0 is reserved for Localhost/Loopback).*

---

### 🏠 Private vs. 🌍 Public IP (Crucial for Hackers)
This is the most important concept I learned today.

#### 1. Private IP (Inside the House)
* Only works **inside** my Local Network (LAN).
* Assigned by my **Router**.
* **Common Range:** `192.168.x.x` or `10.x.x.x`.
* **Security:** Outsiders cannot see or hack this directly.

#### 2. Public IP (Outside World)
* Works on the **Internet**.
* Assigned by my **ISP** (Jio/Airtel).
* **Security:** This is my digital identity. If a hacker gets my Public IP, they can find my rough location (City/ISP) or attack my router.

> **Analogy:**
> * **Private IP** is like my Bedroom Number (Room 2). Meaningless outside my house.
> * **Public IP** is my Home Address (123, MG Road, Mumbai). Anyone can send mail here.

---

### 🧪 Hands-on Lab: Finding My Two Identities
I checked both my IPs to see the difference.

**Step 1: Check Private IP (Linux)**
```bash
ip a
# Look for 'inet 192.168...' or '10.0...'
```
Step 2: Check Public IP (The Hack) Since ip a only shows local info, I asked an external server to tell me my Public IP.
```bash
curl ifconfig.me
# Output: A completely different number (e.g., 45.12.xx.xx). This is how the world sees me.
```
When I use a VPN, it changes my Public IP so websites/hackers can't track my real location.

My Private IP usually stays 192.168.x.x regardless of VPN.
