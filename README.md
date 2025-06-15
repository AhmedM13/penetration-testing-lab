# 🧪 Penetration Testing Lab — SQLi, IDOR, and Stored XSS Attacks

## 👨‍💻 Author: Ahmed Malik  
**Project Duration:** March 2025 – May 2025  
**Environment:** Windows 10 + bWAPP (Victim), Kali Linux (Attacker)  
**Tools Used:** SQLMap, Burp Suite, XAMPP, Firefox

---

## 📘 Overview
This project was designed to simulate real-world web application attacks in a controlled lab environment. I used bWAPP on a Windows 10 VM as the target and Kali Linux as the attacker's system. The goal was to explore how three core vulnerabilities—**SQL Injection (SQLi)**, **Insecure Direct Object Reference (IDOR)**, and **Cross-Site Scripting (XSS)**—can be discovered and exploited using free tools.

---

## 🛠️ Lab Environment

### 🖥️ Victim Machine (Windows 10)
- Installed [XAMPP v5.6.40](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/5.6.40/)
- Hosted [bWAPP vulnerable app](https://sourceforge.net/projects/bwapp/files/bWAPP/bWAPPv2.2/)
- Applied fixes to `install.php` for compatibility with legacy PHP functions

### 🐱‍💻 Attacker Machine (Kali Linux)
- Installed latest Kali ISO and set static IP: `192.168.110.25`
- Used Burp Suite and SQLMap to conduct attacks

---

## 📡 Network Setup
- Configured both VMs on `intnet` network
- Set static IPs for connectivity
- Enabled ping via Windows Firewall (ICMP Echo rule)

---

## 🚨 Attacks Performed

### 1. 🔓 SQL Injection (SQLi)
- Used Burp Suite to intercept POST request from `bWAPP`
- Saved request as `sqli13post.txt`
- Ran `sqlmap` with the following flags:
- Enumerated the `bWAPP` database
- Extracted contents of the `users` table, including:
- Admin: `bee : bug`
- Test account: `test : 1234`

### 2. 🛠️ Insecure Direct Object Reference (IDOR)
- Intercepted `Reset Secret` form using Burp
- Modified request to reset another user’s secret value
- Confirmed via SQLMap that the change was successful

### 3. 🐛 Stored Cross-Site Scripting (XSS)
- Injected this payload via Burp Suite:
  ```html
  <script>alert("Security Alert: Visit https://fix-account.example.com");</script>
  ```
- Payload was stored and triggered in the victim’s browser, demonstrating a successful phishing vector

---

## 📷 Images and Full Report

🖼️ Selected screenshots from this project can be found in the [`/images`](./images) folder.  
📄 For the complete walkthrough, including **all commands**, **outputs**, and **detailed attack steps**, please refer to the full report


## 📘 Lessons Learned
- How SQLMap can automate injection exploitation using captured POST data
- Importance of validating user access (IDOR bypass)
- Real-world implications of persistent (stored) XSS
- Common misconfigurations in legacy PHP/MySQL web apps

---

## ⚠️ Disclaimer
This project was conducted in a controlled virtual lab for educational purposes only.  
Do **not** attempt to exploit vulnerabilities on systems you don’t own or have explicit permission to test.
