# soc-lab-wazuh
A virtual SOC lab using Wazuh to simulate real-world cybersecurity monitoring and attack detection.

---

## 📌 Overview

This self-contained Security Operations Center (SOC) lab was built to gain practical experience in:

- Deploying a SIEM system using **Wazuh**
- Monitoring logs from **Windows, Linux, firewall**, and **web applications**
- Simulating real-world **cyberattacks** from Kali Linux
- Investigating alerts and writing custom detection rules

All components are virtualized using VMware and configured on an isolated network.

---

## 🧱 Lab Architecture

| Component          | Role                              | OS/Tool      |
|-------------------|------------------------------------|--------------|
| Wazuh Server       | SIEM + log aggregation             | Ubuntu 22.04 |
| Windows Endpoint   | Simulated client + agent logs      | Windows 10   |
| Ubuntu DVWA Server | Vulnerable web server + agent      | Ubuntu 22.04 |
| pfSense Firewall   | Log source (remote syslog)         | pfSense      |
| Kali Linux         | Attack simulation                  | Kali Linux   |

📊 See [architecture/lab-diagram.png](architecture/lab-diagram.png) for network layout.

---

## ⚙️ Tools & Technologies

- **SIEM:** Wazuh
- **Virtualization:** VMware Workstation
- **Firewall:** pfSense
- **Attacking Tools:** Nmap, sqlmap, Burp Suite, Hydra
- **Web App:** DVWA (Damn Vulnerable Web Application)
- **Log Forwarding:** Syslog

---

## 🚀 Attack Scenarios

| Scenario            | Description                           |
|---------------------|---------------------------------------|
| SQL Injection       | Attacking DVWA input fields           |
| Brute Force Attack  | Login attempts using Hydra            |
| Reverse Shell       | Gaining shell access via DVWA         |

See detailed guides in [`/attack-scenarios`](attack-scenarios/)

---

## 🔍 Alerts & Detection

Wazuh alerts were triggered by simulated attacks and include:

- Failed login attempts
- SQL injection attempts
- Unauthorized shell access

Custom rules were also written. See [`logs-and-alerts/custom-rules.md`](logs-and-alerts/custom-rules.md)

---

## 📸 Screenshots

- Wazuh Dashboard  
- Alert Logs  
- DVWA Interface  
See [`logs-and-alerts/screenshots/`](logs-and-alerts/screenshots/)

---

## 📘 Setup Guides

Reproducible setup instructions are in the [`/setup-guides`](setup-guides/) folder:

- Wazuh Server
- Windows Endpoint
- Ubuntu + DVWA
- pfSense Firewall
- Kali Linux Attacker

---

## 🧠 Lessons Learned

- Importance of centralized log management
- Writing detection rules based on observed attack patterns
- Basic SOC workflows (collect, analyze, alert)

See [`conclusions/lessons-learned.md`](conclusions/lessons-learned.md)

---

## ✅ Skills Gained

- SOC analysis
- SIEM (Wazuh)
- Log analysis & correlation
- Basic pentesting
- Syslog forwarding
- Windows & Linux system monitoring

---

## 📄 License

This project is licensed under the MIT License. See [`LICENSE`](LICENSE) for more info.
