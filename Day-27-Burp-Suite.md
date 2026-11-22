# 🕵️ Day 27: Burp Suite (The Hacker's Middleman)

**Date:** 22 Nov 2026

Day 26 mein maine seekha ki browser aur server **HTTP** mein baat karte hain.
Aaj ka sawaal: *Kya main is baat-cheet ko beech mein rok kar padh sakta hoon aur badal sakta hoon?*
Jawab hai **haan**, aur iske liye tool hai **Burp Suite**. 🔥

Burp Suite web hacking ka sabse important tool hai. Har pentester aur bug bounty hunter isse roz use karta hai.

---

### 🧠 What is a Proxy?
**Proxy** ek beech wala aadmi hai. Browser seedha server se baat nahi karta, pehle proxy ke paas jata hai.

```text
Normal:      Browser  ─────────────────────────►  Server

With Burp:   Browser  ──►  Burp Suite (Proxy)  ──►  Server
                              ▲
                        Main yahan request
                        padh/badal sakta hoon
```

Real-life analogy: 📮
* **Browser** = Letter likhne wala
* **Server** = Letter paane wala
* **Burp** = Post office ka wo aadmi jo letter khol kar padh sakta hai, badal sakta hai, aur fir aage bhej sakta hai

Burp by default **`127.0.0.1:8080`** par sunta hai (Day 15: port 8080, Day 13: 127.0.0.1 = localhost, yaani mera apna computer).

---

### 📦 Burp Suite Editions

| Edition | Price | Kiske liye |
| :--- | :--- | :--- |
| **Community** | Free | Seekhne ke liye (main yahi use kar raha hoon) |
| **Professional** | Paid | Bug bounty / pentesters (Scanner, fast Intruder) |
| **Enterprise** | Paid | Companies ke automatic scans |

Kali Linux mein Burp Community pehle se installed aata hai:
```bash
burpsuite
```

---

### ⚙️ Setup (Sabse Easy Tareeka)
Pehle log Firefox mein proxy settings aur certificate manually lagate the. Ab Burp ka **built-in browser** hai, jo already setup hota hai.

1. Burp kholo → **Temporary project** → **Use Burp defaults** → **Start Burp**
2. **Proxy** tab → **Intercept** → **Open browser**
3. Ab is browser mein jo bhi website khologe, uski har request Burp se hokar jayegi ✅

---

### 🗂️ Burp ke Main Tabs

| Tab | Kaam | Simple Bhasha Mein |
| :--- | :--- | :--- |
| **Proxy → Intercept** | Request ko beech mein rokna | "Ruko! Pehle main dekhunga." |
| **Proxy → HTTP history** | Saari requests ki list | CCTV recording 📹 |
| **Repeater** | Ek request ko baar-baar badal kar bhejna | Ek hi sawaal alag-alag tareeke se poochhna |
| **Intruder** | Ek request ko hazaron payloads ke saath bhejna | Automatic brute force (Community mein slow hai) |
| **Decoder** | Encode/Decode (URL, Base64, Hex) | Translator 🔤 |
| **Comparer** | Do responses ka difference dekhna | "Spot the difference" game |
| **Target → Site map** | Website ka poora structure | Website ka naksha 🗺️ |

---

### 🚦 Intercept Kaise Kaam Karta Hai

| Button | Kya Hota Hai |
| :--- | :--- |
| **Intercept is on** | Har request ruk jayegi, main usse dekh/badal sakta hoon |
| **Forward** | Request (badli hui ya waisi hi) server ko bhej do |
| **Drop** | Request ko phenk do, server tak jayegi hi nahi |
| **Intercept is off** | Requests bina ruke jayengi (par HTTP history mein save hongi) |

💡 **Tip:** Intercept hamesha on mat rakho, warna har image aur script ki request rukegi aur browser atka hua lagega. Zyada time **HTTP history** use karo, aur jo request interesting lage use **Repeater** mein bhejo (Right click → *Send to Repeater* ya `Ctrl + R`).

---

### 🧪 Hands-on Lab 1: Request Pakdo aur Badlo
**Target:** TryHackMe ka room *Burp Suite: The Basics* (authorized practice environment)

Steps:
1. Burp ke browser mein target website khola.
2. **Intercept on** kiya aur website par ek form submit kiya.
3. Request Burp mein ruk gayi. Isme maine Day 26 wali cheezein pehchaani: **Method, Path, Host, Cookie, Body**.
4. Ek parameter ki value badli aur **Forward** kiya.
5. Response mein dekha ki server ne badli hui value accept ki ya nahi.

**My Screenshot:**
```text
(Screenshot will be added after running the lab)
```

**Maine kya notice kiya:**
```text
(Notes will be added after running the lab)
```

---

### 🧪 Hands-on Lab 2: Python Script ko Burp se Chalana (Day 26 Connection)
Kal ka `http_inspector.py` seedha server se baat karta tha. Aaj maine Python ki requests ko bhi **Burp ke through** bheja, taaki unhe Burp mein dekh sakun.

**Script:** `burp_proxy_test.py`
```python
import sys
import requests
import urllib3

# Burp apna certificate use karta hai, isliye HTTPS warning band ki
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

BURP = "http://127.0.0.1:8080"
proxies = {"http": BURP, "https": BURP}

if len(sys.argv) != 2:
    print("Syntax: python3 burp_proxy_test.py <url>")
    sys.exit()

url = sys.argv[1]

try:
    # verify=False: Burp beech mein hai, isliye certificate check skip
    response = requests.get(url, proxies=proxies, verify=False, timeout=10)
    print(f"✅ Status: {response.status_code}")
    print("👀 Ab Burp → Proxy → HTTP history mein ye request dekho!")

except requests.exceptions.ProxyError:
    print("❌ Burp nahi chal raha! Pehle Burp Suite start karo (port 8080).")
except requests.exceptions.ConnectionError:
    print("❌ Server se connect nahi ho paya.")
except KeyboardInterrupt:
    print("\n🚫 Stopped by user.")
```

🏃‍♂️ **How I ran it:**
```bash
python3 burp_proxy_test.py http://example.com
```

**My Output:**
```text
(Output will be added after running the lab)
```

⚠️ `verify=False` sirf apne lab/testing ke liye hai. Real tools mein certificate check band karna khatarnak hai, kyunki tab koi bhi beech mein baith kar data padh sakta hai (Man-in-the-Middle). Aur aaj maine khud wahi kiya, bas apne hi computer par. 😄

---

### 📝 Hacker's Perspective
1. **Browser ki checks bekaar hain:** Agar form mein JavaScript likhi hai ki "age 18 se kam nahi ho sakti", toh wo check sirf browser mein hai. Burp request ko browser ke **baad** pakadta hai, toh main value kuch bhi kar sakta hoon. Asli security hamesha **server par** honi chahiye.
2. **Hidden fields hidden nahi hain:** Page par na dikhne wale fields (jaise `price=500` ya `role=user`) bhi request mein jaate hain, aur Burp mein main unhe badal sakta hoon.
3. **HTTP history = Recon:** Website use karte waqt history mein dikh jata hai ki kaunse API endpoints, parameters aur cookies use ho rahe hain. Bug hunting yahin se shuru hoti hai.

⚖️ **Rule:** Burp sirf un websites par use karna hai jahan permission ho (TryHackMe, PortSwigger labs, apni website, ya bug bounty program jo allow kare).

---

### 🛠️ Homework
* [ ] TryHackMe room complete karo: **Burp Suite: The Basics**
* [ ] Kisi bhi practice site par 10 minute browse karo aur **HTTP history** mein 3 interesting requests dhoondo (jisme parameters ya cookies ho).
* [ ] **Decoder** mein `SGFja2VyIEp1bmVk` ko Base64 se decode karo. Kya likha hai? 😉

---

**Next Up:** Tomorrow, I will learn **Burp Repeater** in depth and use it to solve my first PortSwigger lab: **Path Traversal** (`../../../etc/passwd`). Day 2 ka Linux file system wala gyaan wahan kaam aayega! 📂
