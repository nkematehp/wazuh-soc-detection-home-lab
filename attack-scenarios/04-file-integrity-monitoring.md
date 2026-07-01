# File Integrity Monitoring

## Objective

The objective of this scenario was to simulate unauthorized file system changes on a monitored Ubuntu server to evaluate Wazuh's File Integrity Monitoring (FIM) capabilities.

## Target

| Property | Value |
|----------|-------|
| Target Host | ubuntu-server |
| Target IP Address | 192.168.211.157 |
| Operating System | Ubuntu Server 24.04 LTS |
| Monitoring Agent | Wazuh Agent |
| Log Source | File Integrity Monitoring (Syscheck) |

## Attack Machine

| Property | Value |
|----------|-------|
| Host | ubuntu-server |
| Tool | Bash Terminal |

## MITRE ATT&CK

| Tactic | Technique | Technique ID |
|----------|-----------------------------------------------|--------------|
| Defense Evasion | File and Directory Modification | T1222 |
| Impact | Data Destruction | T1485 |

## Attack Overview

File Integrity Monitoring (FIM) is used to detect unauthorized changes to monitored files and directories. Attackers frequently create, modify, rename, or delete files while establishing persistence, hiding malicious artifacts, or destroying evidence.

During this scenario, several file operations were performed within a monitored directory to simulate suspicious file activity.

## Attack Execution

The following commands were executed on the Ubuntu server.

```bash
mkdir -p ~/fim-lab

echo "Original content" > ~/fim-lab/confidential.txt

echo "Unauthorized modification" >> ~/fim-lab/confidential.txt

mv ~/fim-lab/confidential.txt ~/fim-lab/secrets.txt

rm ~/fim-lab/secrets.txt
```

These commands generated file integrity events that were collected by the Wazuh Agent and forwarded to the Wazuh Manager for analysis.

## Expected Outcome

The performed file operations were expected to generate File Integrity Monitoring alerts within the Wazuh Dashboard, demonstrating Wazuh's ability to detect file creation, modification, renaming, and deletion.

## Screenshot

![File Integrity Monitoring](../screenshots/file-integrity-monitoring-alerts.png)

## Related Investigation

- [File Integrity Monitoring Investigation](../investigations/04-file-integrity-monitoring.md)