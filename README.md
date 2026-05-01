# phishing-detector
PhishGuard is a browser-based phishing detection tool built with HTML, CSS, and JavaScript that evaluates URLs using rule-based analysis to identify potential security threats.

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


