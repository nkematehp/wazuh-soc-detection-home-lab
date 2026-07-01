# Windows Endpoint Setup

## Prerequisites

### Downloads

- Windows 10 ISO  
  https://www.microsoft.com/software-download/windows10

## VM Configuration

| Setting | Value |
|---------|-------|
| Hostname | windows-endpoint |
| Operating System | Windows 10 Home |
| Firmware | UEFI |
| CPU | 2 vCPU |
| Memory | 3 GB RAM |
| Storage | 40 GB HDD |
| IP Address | 192.168.211.158 |
| Username | Nkemateh Princewill |

## Installation

1. Create a new virtual machine in VMware Workstation.
2. Configure the VM:
   - 2 vCPU
   - 3 GB RAM
   - 40 GB HDD
   - UEFI firmware
3. Install Windows 10 Home.
4. Skip product key activation.
5. Create the local user account `Nkemateh Princewill`.
6. Complete the installation.

## VMware Tools

Install VMware Tools to improve virtual machine performance and usability.

1. In VMware Workstation, select:

   ```text
   VM → Install VMware Tools
   ```

2. Open the VMware Tools DVD drive.
3. Run:

   ```text
   setup.exe
   ```

4. Select **Typical Installation**.
5. Restart the virtual machine.

**Benefits**

- Full-screen support
- Dynamic screen resizing
- Clipboard sharing
- Improved mouse integration

## Next Step

Install and configure the Wazuh Agent and Sysmon:

```text
setup/agent-deployment.md
```