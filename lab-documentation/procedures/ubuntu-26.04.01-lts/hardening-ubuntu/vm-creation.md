# Ubuntu 26.04.1 LTS VM Creation
 
## Overview
 
This document describes the deployment and initial configuration of the **hardening-ubuntu** virtual machine. The VM serves as the baseline system for security auditing, hardening activities, and before-and-after security comparisons performed as part of Module 3.
 
---
 
## Objective
 
Create an Ubuntu 26.04.1 LTS Desktop virtual machine to serve as a controlled laboratory environment for:
 
- Security assessments
- System hardening activities
- Configuration validation
- Baseline and post-hardening comparisons
 
---
 
## Virtual Machine Creation
 
### General Configuration
 
- **VM Name:** hardening-ubuntu
- **Operating System:** Ubuntu 26.04.1 LTS Desktop
- **Platform:** Oracle VirtualBox
 
The virtual machine was created in Oracle VirtualBox using the Ubuntu 26.04.1 LTS Desktop installation media.

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-35-10.png)
 
### Assigned Resources
 
- **Memory:** 4096 MB
- **CPU:** 2 vCPU
- **Disk Size:** 40 GB
- **Disk Format:** Dynamic VDI

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-33-54.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-39-28.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-06%2012-34-52.png)

 
### Justification
 
Resources were allocated to provide a stable environment capable of running Ubuntu Desktop, security assessment tools and future hardening activities while maintaining efficient host resource utilization.
 
---
 
## Virtual Hardware Configuration
 
### System
 
- **Chipset:** ICH9
- **UEFI:** Enabled
- **Secure Boot:** Disabled
- **I/O APIC:** Enabled
- **Hardware Clock in UTC:** Enabled
- **TPM:** Not Configured

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-40-50.png)
 
### Justification
 
The virtual hardware configuration was selected to provide a modern and realistic Linux environment while avoiding unnecessary complexity during the initial deployment phase.
 
UEFI support was enabled to emulate modern hardware platforms, while Secure Boot remained disabled to simplify laboratory activities and troubleshooting procedures.
 
### Processor
 
- **CPU:** 2
- **PAE/NX:** Enabled
- **Execution Cap:** 100%
- **Nested VT-x/AMD-V:** Disabled

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-41-00.png)
 
### Justification
 
PAE/NX provides support for modern memory protection mechanisms. Nested virtualization was not required for the objectives of this laboratory.
 
### Display
 
- **Graphics Controller:** VMSVGA
- **Video Memory:** 256 MB
- **3D Acceleration:** Enabled
- **Monitors:** 1
 
### Justification
 
VMSVGA is the recommended graphics controller for Linux guest operating systems in VirtualBox. Additional video memory and 3D acceleration improve the GNOME Desktop experience.
 
### Network
 
- **Adapter 1:** NAT
- **Adapter Type:** Intel PRO/1000 MT Desktop
- **Cable Connected:** Yes
- **Adapter 2:** Disabled

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-45-20.png)
 
### Justification
 
NAT networking was selected to provide Internet connectivity during installation, system updates and future laboratory activities.
 
A Host-Only adapter will be added later when additional virtual machines are available for internal communication testing.
 
### Storage
 
- **Controller:** SATA (AHCI)
- **Disk:** 40 GB Dynamic VDI
- **Installation Media:** ubuntu-26.04.1-desktop-amd64.iso

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-47-03.png)
 
### Justification
 
AHCI is the standard controller for modern SATA storage devices, while dynamic allocation optimizes host storage usage without affecting functionality.
 
---
 
## Operating System Installation
 
### Language Selection
 
- **Language:** Spanish
 
### Keyboard Configuration
 
- **Keyboard Layout:** Spanish
 
### Justification
 
The operating system language and keyboard layout were configured according to the user's native environment to facilitate administration and system interaction during laboratory activities.
 
### Network Configuration
 
- **Connection Type:** Automatic Wired Connection (NAT)
 
### Installation Method
 
- **Method:** Interactive Installation

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-54-11.png)
 
### Applications Selection
 
- **Installation Type:** Default Selection

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-54-51.png)
 
### Justification
 
The default Ubuntu installation profile was selected to establish a clean baseline while minimizing unnecessary software and reducing the initial attack surface.
 
### Additional Software
 
- **Third-Party Software:** No
- **Multimedia Codecs:** No

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-55-53.png)
 
### Justification
 
No proprietary software or additional multimedia packages were installed in order to maintain a clean and reproducible baseline for future security assessments.
 
---
 
## Disk Configuration
 
### Installation Method
 
- Erase Disk and Install Ubuntu

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-56-46.png)
 
### Automatically Created Partitions
 
```text
/boot/efi -> FAT32
/ -> EXT4
```
 
### Applied Configuration

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-05-01.png)
 
Ubuntu automatically generated the required partitions for a UEFI-based installation.
 
### Disk Encryption
 
- Disabled

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2012-57-22.png)
 
### Justification
 
Disk encryption was intentionally not enabled during the initial deployment phase.
 
This allows the system to serve as an unmodified baseline and provides an opportunity to identify the absence of encryption as a security finding during later audit and hardening activities.
 
---
 
## Local Account Creation
 
### Created Account
 
- **Username:** grs

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-03-28.png)
 
### Justification
 
A local account was created to maintain an isolated and reproducible laboratory environment independent of external services.
 
---
 
## System Identity
 
### Hostname
 
```text
hardening-ubuntu
```
 
### Justification
 
A consistent naming convention is maintained throughout the laboratory.
 
```text
Ubuntu : hardening-ubuntu
Windows : hardening-win11
```
 
---
 
## System Validation
 
### Hostname Verification
 
Command:
 
```bash
hostnamectl
```
 
Result:
 
```text
hardening-ubuntu
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-32-28.png)
 
### User Verification
 
Command:
 
```bash
whoami
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-35-23.png)
 
Result:
 
```text
grs
```
 
### Network Verification
 
Command:
 
```bash
ip a
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-34-47.png)
 
Result:
 
```text
IPv4 address assigned successfully through NAT
```
 
### Operating System Verification
 
Command:
 
```bash
lsb_release-a
```
![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-34-25.png)

Result:
 
```text
Ubuntu 26.04.1 LTS
```
 
---
 
## System Updates
 
### Package Repository Refresh
 
Command:
 
```bash
sudo apt update
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-37-59.png)
 
### Package Upgrade
 
Command:
 
```bash
sudo apt upgrade -y
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-39-21.png)
 
### Result
 
```text
System updated successfully
No pending package upgrades
```
 
---
 
## Baseline Snapshot Creation
 
### Snapshot Name
 
```text
M3-BASELINE-CLEAN
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-48-10.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-48-36.png)
 
### Objective
 
Create a stable restore point before performing security assessments and hardening activities.
 
### Recorded State
 
- UEFI enabled
- Secure Boot disabled
- Local account configured
- System updated
- Network connectivity verified
- No hardening measures applied
 
---
 
## Final System State
 
- **VM Name:** hardening-ubuntu
- **Operating System:** Ubuntu 26.04.1 LTS Desktop
- **Username:** grs
- **Hostname:** hardening-ubuntu
- **Updated:** Yes
- **Connectivity Verified:** Yes
- **Snapshot:** M3-BASELINE-CLEAN
- **Status:** Ready for Security Assessment