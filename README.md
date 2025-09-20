# 👋🏽 King Sanders – Cybersecurity Portfolio

**Entry-Level SOC Analyst | Cybersecurity Professional in Training**

Passionate about protecting organizations through threat detection, log analysis, and incident response. Currently completing the Google Cybersecurity Certificate while building a home SOC lab with Linux, Splunk, and Security Onion. Hands-on practice includes analyzing suspicious logins, documenting incidents, and performing basic vulnerability assessments.
I bring consistency, energy, and a growth mindset — ready to contribute to a SOC team on Day One.

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
- Google Cybersecurity Certificate - Assets, Threats, and Vulnerabilities
- Google Cybersecurity Certificate - Sound the Alarm: Detection and Response

## 📊 Projects

### Web Traffic Analysis with Splunk
A security-focused dashboard built from custom web logs to show how I ingest data, write SPL, and design visualizations.

**Data**
- **Index:** `project1`
- **Sourcetype:** `web:logs`
- **File:** `web_logs.log` (sample HTTP access logs)

**Screenshots**

![Web Traffic Analysis Dashboard](project/web-traffic-analysis.png)

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
# 📊 SQL Log Analysis – Detecting Suspicious Logins  

This project simulates a **brute-force login investigation** using SQL queries on employee login data. The goal was to detect failed login attempts, external access, and patterns of compromise.  

---

## Dataset  
A synthetic `employee_logins` table with:  
- `username` – Employee username  
- `login_time` – Timestamp of login  
- `ip_address` – Source IP  
- `status` – SUCCESS / FAILED  

---

## 🔎 Investigations  

### 1. All Login Records  
```sql
SELECT * 
FROM employee_logins
ORDER BY login_time;
```
External Logins (Outside Internal IP Range)
```sql
SELECT id, username, login_time, ip_address, status
FROM employee_logins
WHERE ip_address NOT LIKE '192.168.%'
  AND ip_address NOT LIKE '10.%'
  AND ip_address NOT LIKE '172.16.%'
ORDER BY login_time;
```
First Failed → First Success (Suspicious Sequence)
```sql
WITH first_failed AS (
  SELECT username, MIN(login_time) AS first_failed_time
  FROM employee_logins
  WHERE status = 'FAILED'
  GROUP BY username
),
first_success AS (
  SELECT username, MIN(login_time) AS first_success_time
  FROM employee_logins
  WHERE status = 'SUCCESS'
  GROUP BY username
)
SELECT f.username, f.first_failed_time, s.first_success_time
FROM first_failed f
JOIN first_success s ON f.username = s.username;
```
Failed Attempts per IP
```sql
SELECT ip_address, COUNT(*) AS failed_count
FROM employee_logins
WHERE status = 'FAILED'
GROUP BY ip_address
ORDER BY failed_count DESC, ip_address;
```
Logins Over Time (by Hour)
```sql
SELECT strftime('%Y-%m-%d %H:00', login_time) AS hour_bucket,
       SUM(CASE WHEN status = 'SUCCESS' THEN 1 ELSE 0 END) AS success_count,
       SUM(CASE WHEN status = 'FAILED' THEN 1 ELSE 0 END) AS failed_count
FROM employee_logins
GROUP BY hour_bucket
ORDER BY hour_bucket;
```
Failed Attempts per User
```sql
SELECT username, COUNT(*) AS failed_attempts
FROM employee_logins
WHERE status = 'FAILED'
GROUP BY username
ORDER BY failed_attempts DESC, username;
```
🚩 Findings

Multiple failed logins from 192.168.1.11 and 10.0.0.5.

User jdoe and admin show repeated failures before eventual success — common in brute-force or credential stuffing attempts.

External logins from 203.0.113.55 (Mary) indicate potential access from outside the corporate network.

✅ Skills Demonstrated

SQL filtering, grouping, and aggregation.

Detecting suspicious authentication patterns.

Identifying external vs internal access.

Translating raw logs into actionable security findings.

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
