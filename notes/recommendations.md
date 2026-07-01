# Recommendations

The following recommendations are based on the observations made throughout this project and are intended to strengthen endpoint security, improve threat detection, and support effective incident response.

## Authentication Security

- Enforce strong password policies across all systems.
- Avoid weak, common, or easily guessed passwords.
- Encourage users to create long and unique passphrases.
- Implement multi-factor authentication (MFA) for administrative accounts.
- Configure account lockout or rate limiting after repeated authentication failures.
- Use SSH key-based authentication instead of password authentication whenever practical.
- Periodically review user accounts for weak or reused credentials.

## Endpoint Security

- Deploy the Wazuh Agent on all critical systems.
- Install Sysmon on Windows endpoints to improve security visibility.
- Regularly review endpoint configurations to reduce unnecessary attack surface.
- Remove unused applications and services.

## File Integrity Monitoring

- Enable File Integrity Monitoring on critical files and directories.
- Continuously monitor configuration files for unauthorized changes.
- Investigate unexpected file modifications, renames, and deletions immediately.
- Periodically review monitored directories to ensure adequate coverage.

## Registry Monitoring

- Monitor Windows Registry Run keys and other persistence locations.
- Investigate unauthorized registry modifications promptly.
- Regularly audit startup entries for suspicious programs.

## Security Monitoring

- Continuously review authentication events for signs of brute-force attacks.
- Monitor discovery activities that may indicate post-compromise reconnaissance.
- Investigate persistence-related alerts immediately.
- Correlate multiple alerts to understand the complete attack sequence rather than treating alerts individually.

## Detection Engineering

- Develop custom Wazuh rules to address organization-specific threats.
- Periodically tune detection rules to reduce false positives.
- Map custom detection rules to the MITRE ATT&CK framework whenever possible.

## System Maintenance

- Keep operating systems and applications up to date with security patches.
- Regularly verify that Wazuh services and agents are operational.
- Review File Integrity Monitoring and Sysmon configurations after major updates.
- Perform routine backups of critical systems and configuration files.

## Future Improvements

Future enhancements to this homelab may include:

- PowerShell abuse detection.
- Wazuh Active Response automation.
- Malware detection scenarios.
- Lateral movement simulations.
- Additional Linux and Windows persistence techniques.
- Threat intelligence integration.
- Email alerting and automated notifications.
- Custom dashboards for SOC monitoring.