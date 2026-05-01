# phishing-detector
PhishGuard is a browser-based phishing detection tool built with HTML, CSS, and JavaScript that evaluates URLs using rule-based analysis to identify potential security threats.
# 🛡️ PhishGuard — Phishing Website Detector

> A professional-grade, browser-based phishing URL detection tool built with pure HTML, CSS, and JavaScript — no backend required.

---

## 🔍 Overview

**PhishGuard** is a client-side phishing URL analyzer built for ethical hackers, security researchers, and cybersecurity students. It simulates how real-world threat intelligence tools analyze URLs for indicators of phishing or malicious activity — all running entirely in the browser with zero server calls.

This project demonstrates:
- URL parsing and structural analysis
- Multi-factor threat scoring
- Real-time browser-style security warnings
- Blacklist cross-referencing

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔐 **HTTPS Check** | Flags sites without SSL/TLS encryption |
| 🚫 **Blacklist Engine** | Cross-references 500+ known phishing domains |
| 🎯 **Keyword Analysis** | Detects phishing trigger words in the URL |
| 📏 **Domain Length Check** | Flags abnormally long domain names |
| 🌐 **TLD Reputation** | Identifies high-risk TLDs (.tk, .ml, .xyz, etc.) |
| 🔤 **Typosquatting Detection** | Catches brand impersonation via Levenshtein distance |
| 🕸️ **Subdomain Depth** | Detects excessive subdomain nesting |
| 🖥️ **Browser-style Warning** | Renders a Chrome/Firefox-like danger page for critical threats |
| 📊 **Threat Score (0–100)** | Quantified risk score with animated meter |
| 🕓 **Scan History** | Tracks last 10 scanned URLs with verdict |
| ⚡ **Scanning Animation** | Step-by-step terminal-style scan log |
| 📱 **Fully Responsive** | Works on mobile, tablet, and desktop |

---

## ⚙️ How It Works

PhishGuard performs **8 independent checks** on every URL and combines their weighted scores into a final **Threat Score (0–100)**:

```
Threat Score 0–19   →  ✅ SAFE
Threat Score 20–59  →  ⚠️ SUSPICIOUS
Threat Score 60–100 →  🚨 DANGEROUS
```

Each check is independent, so even a "clean" domain can trigger warnings if it uses suspicious keywords or a risky TLD.

---

## 🧠 Detection Engine

### 1. HTTPS / Protocol Check (+20 pts)
Checks if the URL uses `https://`. HTTP sites transmit data in plaintext — a major red flag for login pages.

### 2. Blacklist Lookup (+60 pts)
Compares the hostname against a curated list of known phishing and malicious domains including typosquat variants of PayPal, Amazon, Apple, Google, and banking sites.

### 3. TLD Reputation (+25 pts)
Flags domains using high-abuse TLDs:
`.tk .ml .ga .cf .gq .xyz .top .club .online .site .win .racing .loan .stream`

### 4. Phishing Keyword Detection (+10–25 pts)
Scans the full URL for known phishing trigger words:
`login, verify, secure, bank, payment, account, recover, suspend, validate, credential...`

### 5. Domain Length Analysis (+15 pts)
Domains longer than **30 characters** are flagged. Phishers pad domains to obscure the real site name.

### 6. Subdomain Depth (+15 pts)
More than **2 subdomain levels** is suspicious. Classic attack: `paypal.com.secure.login.attacker.xyz`

### 7. IP Address as Hostname (+30 pts)
Legitimate websites use domain names. Raw IP addresses like `http://192.168.1.1/login` are a strong phishing indicator.

### 8. Typosquatting Detection (+35 pts)
Uses **Levenshtein distance algorithm** to detect 1-character differences from trusted brands:
- `paypa1.com` → PayPal
- `arnazon.com` → Amazon
- `micros0ft.com` → Microsoft

---

## 📁 Project Structure

```
phishguard/
│
├── phishing-detector.html    # Main application (self-contained)
├── README.md                 # Project documentation
└── requirements.txt          # Dependencies (all CDN-based)
```

> Since this is a pure frontend project, all logic lives in a single HTML file. No build tools or package managers are needed.

---

## 🚀 Usage

### Option 1 — Open Directly (Recommended)
```bash
# Just open in any modern browser
open phishing-detector.html
# or
double-click phishing-detector.html
```

### Option 2 — Serve Locally
If you want to run it on a local server:

```bash
# Python 3
python -m http.server 8080

# Python 2
python -m SimpleHTTPServer 8080

# Node.js (npx)
npx serve .

# Then open:
# http://localhost:8080/phishing-detector.html
```

### Option 3 — VS Code Live Server
1. Install the **Live Server** extension in VS Code
2. Right-click `phishing-detector.html`
3. Select **"Open with Live Server"**

---

## 🧪 Example URLs to Test

| URL | Expected Result |
|---|---|
| `https://www.google.com` | ✅ SAFE |
| `https://github.com` | ✅ SAFE |
| `http://secure-login-paypal-verify.xyz/account` | ⚠️ SUSPICIOUS / 🚨 DANGEROUS |
| `http://bankofamerica-login-secure.tk/verify-now` | 🚨 DANGEROUS |
| `http://paypa1.com/signin` | 🚨 DANGEROUS (typosquat) |
| `http://192.168.1.1/login` | 🚨 DANGEROUS (bare IP) |
| `http://amazon.secure.login.verify.xyz/account` | 🚨 DANGEROUS |

---

## 🖥️ Browser Compatibility

| Browser | Supported |
|---|---|
| Chrome 90+ | ✅ |
| Firefox 88+ | ✅ |
| Edge 90+ | ✅ |
| Safari 14+ | ✅ |
| Opera 76+ | ✅ |

---

## 🔮 Future Improvements

- [ ] VirusTotal API integration for live threat intelligence
- [ ] WHOIS lookup for domain age analysis (new domains = higher risk)
- [ ] Certificate transparency log checking
- [ ] Machine learning model for URL classification
- [ ] Browser extension version (Chrome/Firefox)
- [ ] Export scan reports as PDF
- [ ] Real-time CVE/blacklist feed updates

---

## ⚠️ Ethical Disclaimer

This tool is built **strictly for educational purposes and ethical security research**. It is intended to:

- Help users identify potentially malicious URLs
- Demonstrate phishing detection techniques
- Support cybersecurity education and awareness

**Do NOT use this knowledge to create phishing sites or harm others.** Unauthorized use against real users or systems is illegal and unethical.

Always obtain proper authorization before conducting any security testing.

---

## 👨‍💻 Author

Built with ❤️ for the ethical hacking community.

> *"Think like an attacker. Defend like a pro."*

---


