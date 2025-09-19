# 👋🏽 King Sanders – Cybersecurity Portfolio

**Aspiring Cybersecurity Analyst**  
Currently working through the Google Cybersecurity Professional Certificate  
Passionate about ethical hacking, Linux, cloud security, and staying curious.

---

## 🧠 Skills & Tools

- Linux basics & command-line
- SQL for data analysis & log queries
- Cybersecurity tools: nmap, wireshark, whois, etc.
- Hands-on labs from Google course
- Constant learner (Darknet Diaries + daily study grind)

---

## 📂 Portfolio Contents

### 🔐 Certifications
- Google Cybersecurity Certificate – Foundations of Cybersecurity
- Google Cybersecurity Certificate – Tools of the Trade: Linux and SQL
- Google Cybersecurity Certificate - Connect and Protect: Networks and Network
Security
- Google Cybersecurity Certificate - Play It Safe: Manage Security Risks

## 📊 Projects

### Web Traffic Analysis with Splunk
A security-focused dashboard built from custom web logs to show how I ingest data, write SPL, and design visualizations.

**Data**
- **Index:** `project1`
- **Sourcetype:** `web:logs`
- **File:** `web_logs.log` (sample HTTP access logs)

**Screenshots**
![Web Traffic Dashboard](CyberBeastKing.github.io/project
/web-traffic-analysis.png)

---

### SPL used for the panels

#### 1) HTTP Status Codes (single-value or bar)
```spl
index=project1 sourcetype=web:logs
| stats count by status
| sort - count

Requests by URL (table or bar)
index=project1 sourcetype=web:logs
| stats count by url
| sort - count

Requests Over Time by Status (timechart/line)
index=project1 sourcetype=web:logs
| timechart span=10m count by status

(Optional) Top Source IPs (table)
index=project1 sourcetype=web:logs
| stats count by src_ip
| sort - count
```




### 🧪 Labs
- Linux permissions lab (chmod, chown, users)
- SQL practice queries (filtering logs, incident data)
- TryHackMe exercises (coming soon)

### 📓 Notes
- Course notes from each module
- Handwriting notes from each module
- Learning journal / progress tracker

---

## 📌 Current Goals
- Finish Google Cybersecurity Cert
- Build a home lab with Kali Linux
- Learn basic penetration testing
- Play It Safe: Manage Security Risks

---

> "I failed. I learned." – That’s my mindset.
