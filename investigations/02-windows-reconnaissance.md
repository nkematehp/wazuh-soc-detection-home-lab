# Incident Report: Windows Reconnaissance

## Summary

| Field | Detail |
|-------|--------|
| Incident Type | Windows Reconnaissance |
| Severity | Low |
| MITRE ATT&CK | T1087, T1082, T1016, T1057, T1046, T1059.001 |
| Affected Host | windows-endpoint (192.168.211.158) |
| Detection Source | Wazuh Dashboard |
| Status | Investigated |

## Detection

Wazuh detected multiple Windows reconnaissance commands executed from PowerShell. The activity was captured by Sysmon and forwarded to the Wazuh Manager for analysis.

### Detection Rules

| Rule ID | Level | Description |
|---------|------:|-------------|
| 92031 | 3 | Discovery activity executed |
| 92033 | 3 | Discovery activity spawned via PowerShell |

## Investigation

### Timeline

| Stage | Activity |
|-------|----------|
| Command Execution | Windows reconnaissance commands executed |
| Telemetry Collection | Sysmon captured the process activity |
| Detection | Wazuh generated discovery alerts |
| Investigation | Alerts reviewed in the Wazuh Dashboard |

### Findings

- Multiple native Windows discovery commands were executed.
- Sysmon captured the process creation events.
- Wazuh correlated the activity and mapped it to the MITRE ATT&CK framework.
- No privilege escalation, persistence, or data exfiltration was observed.

### Indicators of Compromise (IOCs)

| Indicator | Value |
|-----------|-------|
| Host | windows-endpoint |
| IP Address | 192.168.211.158 |
| Process | Windows PowerShell |
| Activity | Windows Reconnaissance |
| MITRE ATT&CK | T1087, T1082, T1016, T1057, T1046, T1059.001 |

## Impact Assessment

| Category | Assessment |
|----------|------------|
| Availability | No impact |
| User Enumeration | Observed |
| System Information | Enumerated |
| Network Configuration | Enumerated |
| Process Enumeration | Observed |

## Recommendations

- Continue monitoring PowerShell activity.
- Restrict unnecessary administrative access.
- Keep Sysmon enabled and properly configured.
- Review reconnaissance alerts during threat hunting.

## Lessons Learned

Wazuh successfully detected Windows reconnaissance activity using Sysmon telemetry, providing enough context to identify and investigate the executed discovery commands.

## Evidence

![Windows Reconnaissance](../screenshots/windows-reconnaissance-alerts.png)

## Related Attack Scenario

- [Windows Reconnaissance](../attack-scenarios/02-windows-reconnaissance.md)