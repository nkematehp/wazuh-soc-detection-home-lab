# Monitoring Server Setup

## Prerequisites

### Downloads

* Ubuntu Server 24.04 LTS ISO  
  https://ubuntu.com/download/server

## VM Configuration

| Setting | Value |
|---------|-------|
| Hostname | monitoring-server |
| Operating System | Ubuntu Server 24.04 LTS |
| CPU | 2 vCPU |
| Memory | 4 GB RAM |
| Storage | 80 GB HDD |
| IP Address | 192.168.211.156 |
| Username | efuet |

## Installation

1. Create a new virtual machine in VMware Workstation.
2. Install Ubuntu Server 24.04 LTS.
3. Configure the VM:
   * 2 vCPU
   * 4 GB RAM
   * 80 GB HDD
4. Set the hostname to `monitoring-server`.
5. Create the user account `efuet`.
6. Enable **OpenSSH Server** during installation.

## System Update

Update the server after installation.

```bash
sudo apt update
sudo apt upgrade -y
sudo reboot
```

## SSH Access

Connect to the monitoring server:

```bash
ssh efuet@192.168.211.156
```

## Next Step

Install and configure Wazuh:

```text
setup/wazuh-installation.md
```