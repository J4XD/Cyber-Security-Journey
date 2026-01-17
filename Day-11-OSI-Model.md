# 🧱 Day 11: The OSI Model (Foundation of Networking)

**Date:** 17 Jan 2026

Today, I learned the **OSI (Open Systems Interconnection)** Model. It is a conceptual framework that explains how data moves from one computer to another over a network. It divides the complex process into **7 Layers**.

> **Mnemonic to Remember:** **P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way.
> (Physical, Data Link, Network, Transport, Session, Presentation, Application).

### 🏛️ The 7 Layers (Bottom to Top)

| Layer # | Name | What it does? (Simple Terms) | Devices/Protocols | Hacker's Attack ⚔️ |
| :--- | :--- | :--- | :--- | :--- |
| **Layer 1** | **Physical** | Transmission of raw bits (0s and 1s) over cables or WiFi. | Cables, Hubs, WiFi Signals | Cutting wires, Signal Jamming. |
| **Layer 2** | **Data Link** | Identifies devices using **MAC Addresses**. Handles physical addressing. | **Switches**, MAC Address | **ARP Spoofing**, MAC Flooding. |
| **Layer 3** | **Network** | Handles logical addressing (**IP Addresses**) and routing (finding the best path). | **Routers**, IP, ICMP (Ping) | IP Spoofing, Ping of Death. |
| **Layer 4** | **Transport** | Ensures data delivery. Decides how much data to send (**TCP/UDP**). | TCP, UDP, Ports | Port Scanning (Nmap), DOS attacks. |
| **Layer 5** | **Session** | Establishes, maintains, and terminates connections (Sessions). | APIs, Sockets | Session Hijacking. |
| **Layer 6** | **Presentation** | Translates data formats (Encryption, Compression). e.g., JPG, SSL. | SSL/TLS, JPEG, ASCII | SSL Stripping. |
| **Layer 7** | **Application** | The interface where users interact (Browsers, Apps). | **HTTP, DNS**, FTP, SMTP | **Phishing, SQL Injection, XSS.** |

---

### 📨 Real Life Analogy (The Postman)
To understand this, imagine sending a **Letter**:

1.  **Application (L7):** You write the letter (Data).
2.  **Presentation (L6):** You translate it into a language the receiver understands (Formatting).
3.  **Session (L5):** You decide to call and tell them "I am sending a letter" (Connection).
4.  **Transport (L4):** You choose: Speed Post (UDP) or Registered Post with Receipt (TCP).
5.  **Network (L3):** You write the **House Address** (IP Address) on the envelope.
6.  **Data Link (L2):** The local postman puts it in a van with a **License Plate** (MAC Address) to reach the local post office.
7.  **Physical (L1):** The van drives on the **Road** (Cables/Wire) to deliver it.

---

### 🧠 Why is this crucial for Hacking?
If I want to hack a website, I attack **Layer 7** (Application).
If I want to intercept WiFi traffic, I attack **Layer 2** (Data Link).
Knowing the layer tells me **which tool** to use.

### 📝 Homework
1.  Open Terminal and type `ping google.com`.
    * This is **Layer 3** (ICMP Protocol) working.
2.  Open Browser and visit a website.
    * This is **Layer 7** (HTTP/HTTPS) working.
