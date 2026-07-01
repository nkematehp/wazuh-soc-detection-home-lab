# Wazuh Rule Explanations

This document explains the primary Wazuh detection rules triggered during the attack simulations performed in this project.

## SSH Brute Force

| Rule ID | Level | Description | Purpose |
|---------:|------:|-------------|---------|
| 5710 | 5 | SSHD: Attempt to login using a non-existent user | Detects authentication attempts using usernames that do not exist on the target system. This is commonly observed during brute-force attacks. |
| 5760 | 5 | SSHD: Authentication failed | Detects failed SSH authentication attempts caused by invalid credentials. |
| 5551 | 10 | PAM: Multiple failed logins in a small period of time | Correlates repeated authentication failures within a short time window, indicating a possible brute-force attack. |
| 5712 | 10 | SSHD: Brute force trying to get access to the system | Detects repeated SSH authentication failures and identifies the activity as a brute-force attack. |

---

## Windows Reconnaissance

| Rule ID | Level | Description | Purpose |
|---------:|------:|-------------|---------|
| 92031 | 3 | Discovery activity executed | Detects execution of Windows discovery commands used to gather information about the operating system, users, processes, or network configuration. |
| 92033 | 3 | Discovery activity spawned via PowerShell execution | Detects discovery commands executed through PowerShell and maps the activity to the MITRE ATT&CK framework. |

---

## Registry Persistence

| Rule ID | Level | Description | Purpose |
|---------:|------:|-------------|---------|
| 92302 | 6 | Registry entry to be executed on next logon was modified | Detects modifications to Windows Registry Run keys commonly used for persistence. |
| 92041 | 10 | Value added to registry key has Base64-like pattern | Detects registry values containing encoded or obfuscated data that may indicate defense evasion or malicious persistence. |
| 92203 | 6 | Executable file created by PowerShell | Detects executable or script creation initiated through PowerShell. |
| 92213 | 15 | Executable file dropped in folder commonly used by malware | Detects executable files created in locations frequently abused by attackers. |

---

## File Integrity Monitoring

| Rule ID | Level | Description | Purpose |
|---------:|------:|-------------|---------|
| 554 | 5 | File added to the system | Detects creation of a monitored file. |
| 550 | 7 | Integrity checksum changed | Detects modifications to an existing monitored file by comparing file checksums. |
| 553 | 7 | File deleted | Detects deletion of monitored files or directories. |

---

## MITRE ATT&CK Mapping

The following MITRE ATT&CK techniques were observed throughout this project.

| Technique ID | Technique |
|--------------|-----------|
| T1110 | Brute Force |
| T1087 | Account Discovery |
| T1082 | System Information Discovery |
| T1016 | System Network Configuration Discovery |
| T1057 | Process Discovery |
| T1046 | Network Service Discovery |
| T1059.001 | PowerShell |
| T1547.001 | Registry Run Keys / Startup Folder |
| T1112 | Modify Registry |
| T1222 | File and Directory Modification |
| T1485 | Data Destruction |

---

## Summary

The built-in Wazuh detection rules were sufficient to identify all attack scenarios implemented in this project. No additional custom rules or decoders were required to detect the simulated attacks. The generated alerts provided sufficient telemetry to support incident investigation and were automatically mapped to relevant MITRE ATT&CK techniques where applicable.