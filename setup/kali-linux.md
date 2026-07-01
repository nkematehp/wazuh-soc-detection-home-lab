# Kali Linux Setup

## Prerequisites

### Downloads

* Kali Linux 2025.4 Installer  
  https://www.kali.org/get-kali/

## VM Configuration

| Setting | Value |
|---------|-------|
| Hostname | kali |
| Operating System | Kali Linux 2025.4 |
| CPU | 2 vCPU |
| Memory | 4 GB RAM |
| Storage | 80 GB HDD |
| Username | kali |

## Installation

1. Create a new virtual machine in VMware Workstation.
2. Select the Kali Linux 2025.4 installation image.
3. Configure the VM:
   * 2 vCPU
   * 4 GB RAM
   * 80 GB HDD
4. Install Kali Linux 2025.4.
5. Set the hostname to `kali`.
6. Create the user account `kali`.
7. Reboot the system.

## System Update

Update the system after installation.

```bash
sudo apt update
sudo apt full-upgrade -y
sudo reboot
```

## Purpose

Kali Linux is used as the attack machine to simulate attacks against the monitored endpoints.

## Next Step

Begin the attack scenarios:

```text
attack-scenarios/
```