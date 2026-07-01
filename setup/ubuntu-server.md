# Ubuntu Server Setup

## Prerequisites

### Downloads

* Ubuntu Server 24.04 LTS ISO  
  https://ubuntu.com/download/server

## VM Configuration

| Setting | Value |
|---------|-------|
| Hostname | ubuntu-server |
| Operating System | Ubuntu Server 24.04 LTS |
| CPU | 2 vCPU |
| Memory | 2 GB RAM |
| Storage | 40 GB HDD |
| IP Address | 192.168.211.157 |
| Username | efuet |

## Installation

1. Create a new virtual machine in VMware Workstation.
2. Install Ubuntu Server 24.04 LTS.
3. Configure the VM:
   * 2 vCPU
   * 2 GB RAM
   * 40 GB HDD
4. Set the hostname to `ubuntu-server`.
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

Connect to the Ubuntu server:

```bash
ssh efuet@192.168.211.157
```

## Next Step

Install the Wazuh Agent:

```text
setup/agent-deployment.md
```