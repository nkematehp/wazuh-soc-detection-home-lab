# Lessons Learned

This project provided practical experience in designing, deploying, and evaluating a Wazuh-based Security Information and Event Management (SIEM) homelab for security monitoring and incident investigation.

## Understanding the Attack Lifecycle

The simulated attack scenarios demonstrated that cyber attacks often follow a sequence of activities rather than a single isolated event. Credential access, system reconnaissance, persistence, and unauthorized file modifications each generate different forms of telemetry that can be collected and analyzed by a SIEM platform.

## Importance of Strong Authentication

The SSH brute-force simulation highlighted the risks associated with weak or predictable passwords. Even though Wazuh successfully detected repeated authentication failures, prevention remains the strongest defense. Strong passwords, account lockout policies, and multi-factor authentication significantly reduce the likelihood of successful credential attacks.

## Endpoint Visibility

Deploying Wazuh Agents on both Windows and Ubuntu endpoints provided comprehensive visibility into operating system activities.

Windows monitoring was enhanced through Sysmon, while Ubuntu provided valuable telemetry through authentication logs and File Integrity Monitoring.

## Value of File Integrity Monitoring

File Integrity Monitoring demonstrated how unauthorized file creation, modification, renaming, and deletion can be detected in real time. Monitoring critical files and directories provides an additional layer of defense against unauthorized system changes.

## MITRE ATT&CK Mapping

One of the most valuable capabilities of Wazuh was its automatic mapping of security events to the MITRE ATT&CK framework. This helped categorize attacker behavior and provided additional context during incident investigations.

## Importance of Investigation

Security alerts alone are not sufficient. Reviewing related events, identifying the attack sequence, and understanding attacker behavior are essential steps in determining the true impact of an incident.

## Practical Challenges

Several practical challenges were encountered throughout the project, including:

- Configuring communication between virtual machines.
- Troubleshooting Wazuh service connectivity.
- Resolving dashboard indexing issues.
- Configuring File Integrity Monitoring for custom directories.
- Understanding the interaction between Wazuh Agents, Sysmon, and the Wazuh Manager.

Resolving these issues provided valuable troubleshooting experience and improved understanding of enterprise security monitoring.

## Overall Outcome

This project demonstrated how Wazuh can successfully monitor Windows and Linux systems, detect common attacker techniques, and provide meaningful telemetry for security investigations.

More importantly, it reinforced that effective cybersecurity depends not only on detecting attacks but also on implementing strong preventive controls, maintaining comprehensive logging, and following a structured incident investigation process.