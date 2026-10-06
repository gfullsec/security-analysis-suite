# Windows 11 Pro VM Creation
 
## Overview
 
This document describes the deployment and initial configuration of the **hardening-win11** virtual machine. The VM serves as the baseline system for security auditing, hardening activities, and before-and-after security comparisons performed as part of Module 3.
 
---
 
## Objective
 
Create a Windows 11 Pro virtual machine to serve as a controlled laboratory environment for:
 
- Security assessments
- System hardening activities
- Configuration validation
- Baseline and post-hardening comparisons
 
---
 
## Virtual Machine Creation
 
### General Configuration
 
- **VM Name:** hardening-win11
- **Operating System:** Windows 11 Pro
- **Platform:** Oracle VirtualBox 7.2.6 r172322

The virtual machine was created in Oracle VirtualBox using the Windows 11 installation media shown below.

 
![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2013-59-58.png)
 
### Assigned Resources
 
- **Memory:** 8192 MB
- **CPU:** 2 vCPU
- **Disk Size:** 80 GB
- **Disk Format:** Dynamic VDI

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-01-10.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-02-07.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-03-24.png)
 
### Justification
 
Resources were allocated to provide a stable environment capable of running Windows 11, security assessment tools and future hardening activities without significantly impacting host system performance.
 
---
 
## Virtual Hardware Configuration
 
### System
 
- **TPM:** 2.0
- **UEFI:** Enabled
- **Secure Boot:** Enabled
- **I/O APIC:** Enabled
- **Chipset:** PIIX3

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-05-12.png)

### Justification
 
The default VirtualBox configuration recommended for Windows 11 was maintained.
 
The combination of:
 
- UEFI
- Secure Boot
- TPM 2.0
 
satisfies modern Windows 11 installation requirements while providing a realistic environment for hardening exercises.
 
### Processor
 
- **CPU:** 2
- **PAE/NX:** Enabled
- **Execution Cap:** 100%
- **Nested VT-x/AMD-V:** Disabled

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-07-10.png)
 
### Justification
 
PAE/NX provides support for modern memory protection mechanisms. Nested virtualization was not required for the objectives of this laboratory.
 
### Display
 
- **Graphics Controller:** VBoxSVGA
- **Video Memory:** 128 MB
 
### Justification
 
VirtualBox recommended configuration for Windows operating systems.
 
### Network
 
- **Adapter 1:** NAT
- **Adapter Type:** Intel PRO/1000 MT Desktop (82540EM)
 
### Justification
 
NAT networking was selected to provide Internet connectivity during installation, system updates and future lab activities.
 
### Storage
 
- **Controller:** SATA (AHCI)
- **Disk:** 80 GB Dynamic VDI
- **Installation Media:** Windows11_Client_x64_en-us_26300_9457.iso
 
---
 
## Operating System Installation
 
### Language Selection
 
- **Language:** English (United States)
 
### Justification
 
Most technical resources used throughout the project are published in English, including:
 
- Microsoft Learn
- CIS Benchmarks
- Microsoft Security Baselines
- Security hardening documentation
 
Using an English operating system improves consistency between the system interface and technical documentation.
 
### Regional Configuration
 
- **Region:** Spain
- **Keyboard Layout:** Spanish
 
### Justification
 
This configuration provides compatibility with the physical keyboard while preserving English technical terminology throughout the operating system.
 
---
 
## Selected Edition
 
- **Windows 11 Pro**

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-20-24.png)
 
### Justification
 
Windows 11 Pro provides access to features commonly required during security hardening activities, including:
 
- Group Policy Editor (gpedit.msc)
- Local Security Policy (secpol.msc)
- Local Policies
- Advanced Security Configuration
 
Windows 11 Pro is also the edition most commonly referenced by CIS Benchmarks and Microsoft security guidance.
 
---
 
## Disk Configuration
 
### Installation Method
 
- Clean Installation

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-22-48.png)
 
### Target Disk
 
- Disk 0 Unallocated Space
- 80 GB

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-22-16.png)
 
### Applied Configuration
 
Windows automatically generated the required GPT partitions for a UEFI-based installation.
 
---
 
## Local Account Creation
 
During OOBE, Windows prompted for Microsoft account configuration.
 
A local account was chosen instead.

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-39-33.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-41-57.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-42-59.png)
 
### Procedure
 
A command prompt was launched using:
 
```text
Shift + F10
```
 
The following command was executed:
 
```cmd
start ms-cxh:localonly
```
 
### Result
 
Local account creation became available.
 
- **Username:** grs
 
### Justification
 
The laboratory environment should remain:
 
- Isolated
- Reproducible
- Independent from external cloud services
 
---
 
## System Identity
 
### Hostname
 
```text
hardening-win11
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-37-18.png)
 
### Justification
 
A consistent naming convention is maintained throughout the laboratory.
 
```text
Ubuntu : hardening-ubuntu
Windows : hardening-win11
```
 
---
 
## Initial Privacy Configuration
 
### Applied Settings
 
- **Location:** Disabled
- **Find My Device:** Disabled
- **Diagnostic Data:** Required Only
- **Improve Inking & Typing:** Disabled
- **Personalized Offers:** Disabled

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-46-09.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-46-32.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-47-09.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-47-39.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-48-00.png)

 
### Justification
 
These settings reduce data collection and minimize unnecessary services within a security-focused laboratory environment.
 
---
 
## System Validation
 
### Hostname Verification
 
Command:
 
```powershell
hostname
```
 
Result:
 
```text
hardening-win11
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-49-29.png)
 
### User Verification
 
Command:
 
```powershell
whoami
```
 
Result:
 
```text
hardening-win11\grs
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-49-57.png)
 
### Network Verification
 
Command:
 
```powershell
ipconfig
```
 
Result:
 
```text
IPv4 Address: 10.0.2.15
Gateway: 10.0.2.2
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-50-17.png)
 
### Operating System Verification
 
Command:
 
```text
winver
```
 
Result:
 
```text
Windows 11 Pro
Version 26H2
Build 26300.9457
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-50-44.png)
 
---
 
## System Updates
 
### Windows Update
 
Path:
 
```text
Settings → Windows Update
```
 
### Result
 
```text
System updated successfully
No pending updates
```
 
Final verification:
 
```text
You're up to date
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-55-26.png)
 
---
 
## Baseline Snapshot Creation
 
### Snapshot Name
 
```text
M3-BASELINE-CLEAN-W11
```

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-57-44.png)

![Oracle VirtualBox VM creation wizard](./images/Captura%20desde%202026-10-03%2014-58-17.png)
 
### Objective
 
Create a stable restore point before performing security assessments and hardening activities.
 
### Recorded State
 
- TPM 2.0 enabled
- UEFI enabled
- Secure Boot enabled
- Local account configured
- System fully updated
- Network connectivity verified
- No hardening measures applied
 
---
 
## Final System State
 
- **VM Name:** hardening-win11
- **Operating System:** Windows 11 Pro 26H2
- **Build:** 26300.9457
- **Username:** grs
- **Hostname:** hardening-win11
- **Updated:** Yes
- **Connectivity Verified:** Yes
- **Snapshot:** M3-BASELINE-CLEAN-W11
- **Status:** Ready for Security Assessment