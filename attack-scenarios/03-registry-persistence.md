# Registry Persistence

## Objective

Simulate a Windows Registry Run Key persistence technique and validate Wazuh's ability to detect registry modifications.

## Target

| Property | Value |
|----------|-------|
| Host | windows-endpoint |
| IP Address | 192.168.211.158 |
| Operating System | Windows 10 Home |
| Monitoring Agent | Wazuh Agent |
| Log Source | Sysmon |

## Attack Machine

| Property | Value |
|----------|-------|
| Host | windows-endpoint |
| Tool | Windows PowerShell |

## MITRE ATT&CK

| Tactic | Technique | ID |
|----------|----------------------------------------------|-----------|
| Persistence | Registry Run Keys / Startup Folder | T1547.001 |
| Defense Evasion | Modify Registry | T1112 |
| Execution | PowerShell | T1059.001 |

## Attack Overview

A harmless batch file was created and added to the Windows **Run** registry key to simulate persistence.

## Attack Execution

```powershell
New-Item -ItemType Directory -Path "C:\Temp" -Force

Set-Content -Path "C:\Temp\startup-test.bat" -Value "echo Registry Persistence Test"

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Run" /v StartupTest /t REG_SZ /d "C:\Temp\startup-test.bat" /f

reg query "HKCU\Software\Microsoft\Windows\CurrentVersion\Run"
```

The registry modification generated Sysmon events that were collected and analyzed by Wazuh.

## Expected Outcome

Wazuh generates alerts for the registry modification, allowing the persistence activity to be investigated.

## Evidence

![Registry Persistence](../screenshots/registry-persistence-alerts.png)

## Related Investigation

- [Registry Persistence Investigation](../investigations/03-registry-persistence.md)