# Agent Deployment

## Linux Agent Deployment

### Reference Documentation

https://documentation.wazuh.com/current/installation-guide/wazuh-agent/index.html

### Target System

- ubuntu-server (192.168.211.157)

### Install Wazuh Agent

Add the Wazuh repository:

```bash
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/wazuh.gpg --import

sudo chmod 644 /usr/share/keyrings/wazuh.gpg

echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
```

Install the agent:

```bash
sudo apt update

sudo WAZUH_MANAGER='192.168.211.156' apt install wazuh-agent -y
```

Enable and start the agent:

```bash
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

Verify:

```bash
sudo systemctl status wazuh-agent
```

Expected result:

```text
active (running)
```

---

## Windows Agent Deployment

### Reference Documentation

https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-windows.html

### Install Sysmon

#### Downloads

- Sysmon  
  https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon

- SwiftOnSecurity Sysmon Configuration  
  https://github.com/SwiftOnSecurity/sysmon-config

1. Download and extract Sysmon.
2. Download and extract the SwiftOnSecurity configuration.
3. Copy `sysmonconfig-export.xml` into the Sysmon folder.
4. Open PowerShell as Administrator.
5. Install Sysmon:

```powershell
.\Sysmon64.exe -accepteula -i sysmonconfig-export.xml
```

Verify:

```powershell
Get-Service Sysmon64
```

Expected result:

```text
Status : Running
```

### Install Wazuh Agent

Open the Wazuh Dashboard:

```text
Agents → Deploy New Agent
```

Configure:

```text
Operating System: Windows
Manager Address: 192.168.211.156
```

Run the generated PowerShell installation command as Administrator.

Start the agent:

```powershell
net start wazuh
```

### Configure Sysmon Log Collection

Edit:

```text
C:\Program Files (x86)\ossec-agent\ossec.conf
```

Add:

```xml
<localfile>
  <location>Microsoft-Windows-Sysmon/Operational</location>
  <log_format>eventchannel</log_format>
</localfile>
```

Restart the agent:

```powershell
net stop wazuh
net start wazuh
```

---

## Verification

Verify both agents appear in the Wazuh Dashboard:

- ubuntu-server
- windows-endpoint

Status:

```text
Active
```

Verify Sysmon:

```powershell
Get-Service Sysmon64
```

Expected result:

```text
Status : Running
```

## Screenshots

- Agents Connected
- Wazuh Dashboard

## Next Step

Begin the attack scenarios:

```text
attack-scenarios/
```