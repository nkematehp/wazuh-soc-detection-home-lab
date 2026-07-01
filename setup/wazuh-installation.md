# Wazuh Installation

## Prerequisites

The Wazuh platform was installed on the monitoring server using the official Wazuh installation guide.

### Reference Documentation

https://documentation.wazuh.com/current/installation-guide/index.html

## Target System

| Setting | Value |
|---------|-------|
| Hostname | monitoring-server |
| Operating System | Ubuntu Server 24.04 LTS |
| IP Address | 192.168.211.156 |

## Working Directory

```text
/opt/wazuh-installation
```

## Components Installed

- Wazuh Indexer
- Wazuh Manager
- Filebeat
- Wazuh Dashboard

## Installation Summary

The installation followed the official manual in the following order:

1. Generate certificates.
2. Install Wazuh Indexer.
3. Initialize OpenSearch security.
4. Install Wazuh Manager.
5. Install Filebeat.
6. Install Wazuh Dashboard.
7. Verify all services.

## Verification

Verify the Wazuh services:

```bash
systemctl status wazuh-manager
systemctl status wazuh-indexer
systemctl status wazuh-dashboard
```

Verify Filebeat:

```bash
systemctl status filebeat
filebeat test output
```

Access the Wazuh Dashboard:

```text
https://192.168.211.156
```

## Troubleshooting

During installation, two issues were encountered:

- Wazuh Indexer failed to start due to memory locking requirements. The issue was resolved by updating the systemd override configuration.
- The Wazuh Dashboard initially displayed **"Wazuh dashboard server is not ready yet"**. Updating the dashboard configuration to the correct Indexer address resolved the issue.

## Screenshots

- Wazuh Dashboard
- Wazuh Services

## Next Step

Deploy Wazuh Agents to:

- Ubuntu Server
- Windows Endpoint

```text
setup/agent-deployment.md
```