# 🔐 Wazuh SIEM Lab (SOC Project)

## 📌 Overview

This project demonstrates the deployment, configuration, and practical use of a **Security Information and Event Management (SIEM)** system using Wazuh.

The goal of this lab is to simulate real-world cyber attacks and analyze how a SOC (Security Operations Center) detects and responds to them using log monitoring and alerting.

---

## 🎯 Project Objective

* Deploy a working SIEM environment
* Collect and analyze system and security logs
* Simulate common cyber attacks
* Detect threats using Wazuh rules
* Perform basic incident analysis

---

## 🏗️ Architecture

```
[ Windows Server ] ---> Wazuh Agent  
[ Ubuntu Server ] ---> Wazuh Manager ---> Wazuh Indexer ---> Dashboard  
                        ↑  
                   Log Sources (auth.log, system logs)
```

---

## ⚙️ Setup

* Installed Wazuh Manager, Indexer, and Dashboard
* Configured Wazuh Agent on Windows Server
* Fixed SSL and authentication issues
* Connected all components successfully
* Verified all services are running

---

## ⚔️ Attack Simulation

The following attacks were simulated to generate security events:

* Failed SSH login attempts (Brute-force simulation)
* Invalid user login attempts
* Sudo privilege escalation attempts
* File integrity monitoring (test file creation)

Example commands used:

```
sudo -k
sudo ls (wrong password)
ssh fakeuser@localhost
sudo useradd attacker
touch /etc/test_alert
```

---

## 🚨 Alert Detection

### 🔍 Wazuh Alert Dashboard

![Wazuh Alerts](screenshots/wazuh-alert-dashboard.png)

### Observations:

* Multiple authentication failures detected
* Brute-force attack patterns identified
* Sudo privilege escalation events logged
* Alerts mapped to MITRE ATT&CK techniques

---

## 🧠 Incident Analysis

### 🔴 Incident: SSH Brute Force Attack

**Attack Method:**
Repeated login attempts using an invalid user.

**Logs Observed:**

* Failed password attempts
* Invalid user login messages
* Connection closed after multiple failures

**Wazuh Detection:**

* Rule triggered: Authentication failure
* Alert level: Medium severity

**Analysis:**
This behavior indicates a brute-force attack attempting to gain unauthorized access.

**Impact:**
If successful, attacker could compromise the system.

**Mitigation:**

* Disable password-based SSH login
* Use SSH key authentication
* Implement IP blocking (e.g., Fail2Ban)

---

## 🛠️ Tools Used

* Wazuh SIEM
* Ubuntu Linux
* Windows Server
* SSH
* Filebeat (log forwarding)

---

## 📊 Results

* Successfully generated and monitored real-time alerts
* Detected multiple attack patterns
* Verified alert severity levels in dashboard
* Demonstrated log collection and analysis workflow

---

## 🎓 Skills Gained

* SIEM deployment and configuration
* Log analysis and monitoring
* Security event detection
* Attack simulation techniques
* Basic incident response

---

## 🚀 Future Improvements

* Implement automated response (IP blocking using Fail2Ban)
* Integrate additional log sources (web server, firewall)
* Deploy in cloud environment (AWS)
* Add real-time alert notifications

