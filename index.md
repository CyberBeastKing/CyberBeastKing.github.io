# 👋🏽 King Sanders – Cybersecurity Portfolio
🌐 Portfolio Website: https://cyberbeastking.github.io/

**Entry-Level SOC Analyst | Cybersecurity Professional in Training**

Passionate about protecting organizations through threat detection, log analysis, and incident response. Currently completing the Google Cybersecurity Certificate while building a home SOC lab with Linux, Splunk, and Security Onion. Hands-on practice includes analyzing suspicious logins, documenting incidents, and performing basic vulnerability assessments.

I bring consistency, energy, and a growth mindset — ready to contribute to a SOC team on Day One.

---

## 🧠 Skills & Tools
- Log analysis & incident documentation
- SIEM workflows (Splunk, Security Onion – home lab practice)
- Linux command-line for log navigation & user management
- SQL queries for failed login investigations & device reports
- Network monitoring & packet analysis (Wireshark, tcpdump)
- Cybersecurity tools: nmap, whois, nslookup
- Constant learner (daily labs, podcasts, certifications)

---

## 🔐 Certifications
- [Foundations of Cybersecurity](certifications/coursera-foundations-of-cybersecurity.pdf)
- [Tools of the Trade: Linux and SQL](certifications/coursera-tools-of-the-trade.pdf)
- [Connect and Protect: Networks and Network Security](certifications/coursera-connect-and-protect.pdf)
- [Play It Safe: Manage Security Risks](certifications/coursera-play-it-safe-manage-security-risks.pdf)
- [Assets, Threats, and Vulnerabilities](certifications/Coursera-Assets-Threats-and-Vulnerabilities.pdf)
- [Sound the Alarm: Detection and Response](certifications/Coursera-Sound-the-Alarm-Detection and Response.pdf)

> If any link 404s, double-check the exact PDF filenames and capitalization in `/certifications`.

---

## 📊 Projects

### Project 1 — Web Traffic Analysis with Splunk
A security-focused dashboard built from custom web logs to show how I ingest data, write SPL, and design visualizations.

**Data**
- **Index:** `project1`
- **Sourcetype:** `web:logs`
- **File:** `web_logs.log` (sample HTTP access logs)

**Screenshot**

![Web Traffic Analysis Dashboard](project/web-traffic-analysis.png)

**SPL used (panel highlights)**
```spl
index=project1 sourcetype=web:logs
| stats count by status
| sort - count
