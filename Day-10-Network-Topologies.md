# 🕸️ Day 10: Network Types & Topologies (The Layout)

**Date:** 16 Jan 2026

> **🔔 Note:** Yesterday (Day 9), we used commands like `ip` and `ping` to check connectivity. Today, we start **Phase 2 (Core Networking)** to understand *HOW* these connections are actually built physically.

**Phase 2 Start:** Today, I started learning Networking basics. The first step is understanding how computers are connected physically and logically.

### 🌍 1. Types of Networks (By Size)

| Type | Full Form | Range | Example |
| :--- | :--- | :--- | :--- |
| **LAN** | Local Area Network | Small (Home/Office) | My WiFi connection. All devices in my house are on a LAN. |
| **MAN** | Metropolitan Area Network | City (City-wide) | City Cable TV network or City-wide WiFi. |
| **WAN** | Wide Area Network | Global (World) | **The Internet**. The largest WAN connecting all smaller networks. |
| **PAN** | Personal Area Network | Very Small | Bluetooth Headphones connected to a phone. |

---

### 📐 2. Network Topologies (By Design)
Topology refers to the layout of how devices are connected via cables or signals.

#### **A. Bus Topology 🚌**
* **Concept:** A single central cable (Backbone) connects all computers. Like stops on a single bus route.
* **Security View:** Very unsafe. If I tap into the main wire (Sniffing), I can see everyone's data.
* **Weakness:** If the main cable breaks, the whole network goes down.

#### **B. Star Topology ⭐ (Most Popular)**
* **Concept:** All devices connect to a central device (**Switch/Hub**).
* **Real Life:** My home WiFi. The router is in the center, and all phones/laptops connect to it.
* **Security View:** More secure. To intercept data between two computers, a hacker needs to perform a "Man-in-the-Middle" attack.

#### **C. Ring Topology 💍**
* **Concept:** Computers are connected in a closed loop. Data travels in one direction (Token passing).
* **Weakness:** If one computer fails, the loop breaks, and the network stops.

#### **D. Mesh Topology 🕸️ (The Internet)**
* **Concept:** Every device is connected to every other device (or multiple devices).
* **Security View:** This is how the **Internet** works. If one path is blocked, data finds another route (Redundancy).

---

### 🧠 Why is this important for Hacking?
When attacking a target, I need to know their network structure.
If they are using a **Star Topology** (which 99% of offices use), simple "Sniffing" won't work. I will need to use techniques like **ARP Spoofing** to trick the central Switch.

### 📝 Homework / Observation
1.  Check my home router. It acts as the center of the **Star Topology**.
2.  Visualize how data travels from my Phone -> Router -> ISP -> Internet (Mesh).
