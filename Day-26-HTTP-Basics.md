# 🌐 Day 26: HTTP Basics (How the Web Talks)

**Date:** 22 Nov 2026

### 🔁 Comeback Note
I took a long break after Day 25 (Jan 2026). Today I am restarting my journey.
Phase 1 (Linux), Phase 2 (Networking) and Phase 3 (Python) are done.
**Phase 4: Web Hacking & CTFs starts today.** 🚀

Web hacking ka pehla rule: *Jab tak tum ye nahi samjhoge ki browser aur server aapas mein kaise baat karte hain, tab tak tum unhe hack nahi kar sakte.*
Aur ye baat-cheet hoti hai **HTTP** ke through.

---

### 🧠 What is HTTP?
**HTTP (HyperText Transfer Protocol)** wo language hai jisme Browser (Client) aur Website (Server) baat karte hain.

* **Client:** Jo request bhejta hai (Browser, curl, Python script).
* **Server:** Jo response wapas deta hai (Website ka computer).
* **HTTPS:** HTTP + Encryption (TLS). Data beech mein koi padh nahi sakta.

Real-life analogy: 🍽️
* **Client** = Customer
* **Request** = Order ("Ek chai dena")
* **Server** = Waiter + Kitchen
* **Response** = Chai (ya "Sorry, chai khatam hai" = Error)

Day 15 se connection: HTTP default **Port 80** par chalta hai aur HTTPS **Port 443** par. Dono **TCP** use karte hain.

---

### 🔗 Anatomy of a URL
`https://shop.example.com:443/products/view?id=5&sort=price#reviews`

| Part | Example | Meaning |
| :--- | :--- | :--- |
| **Scheme** | `https` | Kaunsa protocol use hoga |
| **Domain** | `shop.example.com` | Server ka naam (DNS se IP banta hai) |
| **Port** | `443` | Server ka kaunsa darwaza |
| **Path** | `/products/view` | Server par kaunsa page/resource |
| **Query** | `?id=5&sort=price` | Server ko bheje gaye parameters (key=value) |
| **Fragment** | `#reviews` | Sirf browser ke liye, server tak nahi jata |

🎯 **Hacker Note:** Query parameters (`id=5`) user control karta hai. Agar `id=5` ko `id=6` kar diya aur kisi aur ka data dikh gaya, toh wo bug hai (IDOR). Yahi se web hacking shuru hoti hai.

---

### 📤 HTTP Request Structure
Jab browser kisi page ko maangta hai, toh ye bhejta hai:

```http
GET /login HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Cookie: session=abc123
Accept: text/html
```

| Line | Meaning |
| :--- | :--- |
| `GET /login HTTP/1.1` | **Request Line:** Method + Path + Version |
| `Host:` | Kaunsi website chahiye (ek server par kai websites ho sakti hain) |
| `User-Agent:` | Main kaunsa browser/tool hoon |
| `Cookie:` | Meri pehchaan (login session) |
| *(khali line)* | Headers khatam |
| **Body** | Data (sirf POST/PUT mein, jaise username/password) |

---

### 📥 HTTP Response Structure
Server jawab deta hai:

```http
HTTP/1.1 200 OK
Server: nginx/1.18.0
Content-Type: text/html
Set-Cookie: session=xyz789; HttpOnly; Secure

<html> ...page ka content... </html>
```

| Line | Meaning |
| :--- | :--- |
| `HTTP/1.1 200 OK` | **Status Line:** Sab theek hai |
| `Server:` | Server ka software (aur kabhi-kabhi version bhi!) |
| `Content-Type:` | Body kis type ki hai (HTML, JSON, image) |
| `Set-Cookie:` | Server browser ko cookie de raha hai |
| **Body** | Asli page |

---

### 🚦 HTTP Methods

| Method | Kaam | Example |
| :--- | :--- | :--- |
| **GET** | Data maangna | Page kholna |
| **POST** | Data bhejna | Login form submit |
| **PUT** | Data update/replace karna | Profile update |
| **DELETE** | Data delete karna | Post delete |
| **HEAD** | Sirf headers maangna (body nahi) | Server check karna |
| **OPTIONS** | Server kaunse methods allow karta hai | Recon |

---

### 🔢 Status Codes (Server ka Mood)

| Code | Meaning | Hacker ke liye matlab |
| :--- | :--- | :--- |
| **200** OK | Sab sahi | Page mil gaya |
| **301 / 302** Redirect | Kahin aur jao | Login ke baad redirect, open redirect bugs |
| **400** Bad Request | Request galat hai | Mera payload server ko samajh nahi aaya |
| **401** Unauthorized | Pehle login karo | Authentication chahiye |
| **403** Forbidden | Login ho, par permission nahi | Yahan bypass try karte hain 👀 |
| **404** Not Found | Page nahi hai | Directory brute force mein ignore karte hain |
| **500** Server Error | Server crash/error | Mera input ne kuch tod diya, dig deeper! |

Yaad rakhne ki trick:
* **2xx** = ✅ Success
* **3xx** = ↪️ Redirect
* **4xx** = 🙅 Client ki galti
* **5xx** = 💥 Server ki galti

---

### 🍪 Important Headers

| Header | Kaam |
| :--- | :--- |
| **Host** | Kaunsi website |
| **User-Agent** | Client ki pehchaan |
| **Cookie** | Browser server ko cookie wapas bhejta hai |
| **Set-Cookie** | Server browser ko cookie deta hai |
| **Content-Type** | Data ka format |
| **Authorization** | Token / login details |

**Cookie kyun zaroori hai?** HTTP **stateless** hai. Matlab server ko yaad nahi rehta ki aap kaun ho.
Isliye login ke baad server ek **session cookie** deta hai. Har request ke saath browser wo cookie bhejta hai, aur server pehchaan leta hai: "Haan, ye Juned hai."

⚠️ Agar kisi ne meri session cookie chura li, toh wo **bina password ke** mera account use kar sakta hai.

---

### 🧪 Hands-on Lab 1: Seeing HTTP with `curl`
`curl` terminal se HTTP request bhejta hai. `-v` (verbose) se poori baat-cheet dikhti hai.

```bash
curl -v http://example.com
```

Output mein:
* `>` se shuru hone wali lines = **Meri Request** (jo maine bheja)
* `<` se shuru hone wali lines = **Server ka Response** (jo server ne bheja)

**My Output:**
```text
(Output will be added after running the lab)
```

Sirf headers dekhne ke liye (body nahi):
```bash
curl -I https://example.com
```

---

### 🧪 Hands-on Lab 2: HTTP with Python (Day 23 Connection)
Day 23 mein maine `requests` library seekhi thi. Aaj usse HTTP ko samajhne ke liye use kiya.

**Script:** `http_inspector.py`
```python
import sys
import requests

if len(sys.argv) != 2:
    print("Syntax: python3 http_inspector.py <url>")
    sys.exit()

url = sys.argv[1]

try:
    response = requests.get(url, timeout=5)

    print("-" * 50)
    print(f"URL         : {response.url}")
    print(f"Status Code : {response.status_code} {response.reason}")
    print("-" * 50)

    print("\n📥 Response Headers:")
    for key, value in response.headers.items():
        print(f"  {key}: {value}")

    # Hacker check: kya server apna software bata raha hai?
    server = response.headers.get("Server")
    if server:
        print(f"\n🎯 Server header found: {server}")
    else:
        print("\n✅ Server header hidden (good security).")

    # Cookies
    if response.cookies:
        print("\n🍪 Cookies:")
        for cookie in response.cookies:
            print(f"  {cookie.name} = {cookie.value}")

except requests.exceptions.MissingSchema:
    print("❌ URL ke aage http:// ya https:// lagao.")
except requests.exceptions.ConnectionError:
    print("❌ Server se connect nahi ho paya.")
except requests.exceptions.Timeout:
    print("❌ Server ne time par jawab nahi diya.")
except KeyboardInterrupt:
    print("\n🚫 Stopped by user.")
```

🏃‍♂️ **How I ran it:**
```bash
python3 http_inspector.py https://example.com
```

**My Output:**
```text
(Output will be added after running the lab)
```

Isme Day 25 ka **try/except** bhi use hua, taaki galat URL dene par script crash na ho. 💪

---

### 📝 Hacker's Perspective
1. **Server header leak:** `Server: nginx/1.18.0` jaisa header attacker ko exact version bata deta hai. Fir wo us version ke known vulnerabilities (CVE) dhoondh sakta hai. Isliye achhe servers ye header chhupa dete hain.
2. **Cookie = Identity:** Cookie chori matlab account chori. Isliye cookies par `HttpOnly` (JavaScript nahi padh sakti) aur `Secure` (sirf HTTPS par jayegi) flags hone chahiye.
3. **User control everything:** Request ka har hissa (URL, headers, cookies, body) user badal sakta hai. Server ko kabhi bhi client par blindly trust nahi karna chahiye. Yahi web hacking ka base hai.

---

### 🛠️ Homework
* [ ] TryHackMe room complete karo: **HTTP in Detail**
* [ ] 3 alag websites par `curl -I` chalao aur note karo ki kaunsi website `Server` header dikhati hai aur kaunsi chhupati hai.
* [ ] `http_inspector.py` mein ek feature add karo: check karo ki cookies par `HttpOnly` aur `Secure` flags hain ya nahi.

---

**Next Up:** Tomorrow, I will learn **Burp Suite**, a tool that sits between my browser and the server, so I can **catch and modify** these HTTP requests before they reach the server. 🕵️‍♂️
