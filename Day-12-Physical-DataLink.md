# 🔌 Day 12: Physical & Data Link Layers (The Hardware)

**Date:** 18 Jan 2026

Today, I deep-dived into the bottom two layers of the OSI Model. This is where software meets hardware.

### 🧱 Layer 1: The Physical Layer (The Road)
This layer is all about the physical connection. It doesn't care about "Data" or "Logic"; it only cares about **Signals**.
* **Devices:** Cables (Ethernet/Fiber Optic), Hubs, WiFi Signals.
* **Data Form:** **Bits** (0s and 1s).
* **Key Concept (Hub):** A Hub is a "Dumb Device". If it receives data for one computer, it shouts it to *everyone* connected to it. This causes traffic jams (Collisions) and is very insecure.

---

### 🔗 Layer 2: The Data Link Layer (The Identity)
This layer is responsible for delivering data between devices on the **same network** (e.g., inside my house).
* **Devices:** **Switches**, Network Interface Cards (NIC).
* **Data Form:** **Frames**.
* **Key Address:** **MAC Address**.

#### 🆔 What is a MAC Address?
* **Definition:** Media Access Control Address. It is a unique 48-bit physical address "burned" into the network card by the manufacturer.
* **Format:** `00:1A:2B:3C:4D:5E` (6 pairs of hex numbers).
    * **First 3 pairs (OUI):** Identify the Manufacturer (e.g., Apple, Dell, Intel).
    * **Last 3 pairs:** Unique ID for that specific device.
* **Analogy:** If IP Address is your "Home Address" (which can change if you move), MAC Address is your "Fingerprint" (which stays with you).

#### 🔀 Switch vs. Hub (Why Switch is Smart)
* Unlike a Hub, a **Switch** is intelligent. It learns the MAC address of every device connected to it.
* **MAC Table:** The switch keeps a diary (MAC Address Table) mapping Ports to MAC Addresses (e.g., Port 1 = Laptop A, Port 2 = PC B).
* **Result:** When A sends data to B, the Switch sends it *only* to Port 2. No shouting.

---

### ⚔️ Hacker's Perspective (Why do I care?)
1.  **MAC Filtering Bypass:** Many WiFi routers block unknown devices using MAC Filtering. As a hacker, I can change my MAC Address (**Spoofing**) to match a trusted device (like the admin's phone) and gain access.
2.  **MAC Flooding:** I can bombard a Switch with fake MAC addresses. The Switch gets confused and starts acting like a Hub (shouting data to everyone), allowing me to capture traffic.

### 🧪 Hands-on Lab: Finding My Physical Identity
I learned how to check my MAC address in Linux.

**Command:**
```bash
ip link show
```
