# Initial Security Assessment and Baseline

## Overview

This document records the initial security assessment performed on a clean Ubuntu 26.04.1 LTS installation using Lynis as the primary security auditing tool.

The objective of this phase is to establish a security baseline, identify areas for improvement, and classify the recommendations provided by the auditing tool before any hardening measures are applied.

---

## Assessment Objectives

- Establish a security baseline for the system.
- Identify configuration weaknesses.
- Detect services and components that may benefit from hardening.
- Classify recommendations according to risk and impact.
- Define a reference point for future comparisons.

---

## Scope

The assessment was conducted on an Ubuntu 26.04.1 LTS virtual machine created specifically for hardening and validation activities.

### Assessed System

| Item | Value |
|-----------|-----------|
| Operating System | Ubuntu 26.04.1 LTS Desktop |
| Platform | Oracle VirtualBox 7.2.20 |
| Virtual Machine Name | hardening-ubuntu |
| Memory | 4 GB |
| CPU | 2 vCPU |
| Disk | 40 GB Dynamic VDI |

---

## Methodology

The assessment was performed using Lynis 3.1.6 with its default configuration.

### System Preparation

Before executing the audit, the following tasks were performed:

```bash
sudo apt update
sudo apt upgrade -y
```

### Lynis Installation

```bash
sudo apt install lynis -y
```

### Version Verification

```bash
lynis show version
```

Result:

```text
3.1.6
```

---

## Initial Audit

The security audit was executed using the following command:

```bash
sudo lynis audit system
```

The generated results were preserved to maintain a baseline and facilitate future comparisons after hardening measures are applied.

---

## Generated Artifacts

The following artifacts were generated during the initial assessment and stored as evidence of the system baseline:

| File | Description |
|-----------|-----------|
| artifacts/lynis-initial.log | Complete Lynis audit log |
| artifacts/lynis-report-initial.dat | Structured Lynis report containing findings and recommendations |

These files allow future verification of the identified findings and comparison against the results obtained after the hardening phase.

---

## Baseline Results

### Executive Summary

| Metric | Result |
|-----------|-----------|
| Hardening Index | 63 |
| Warnings | 0 |
| Suggestions | 39 |
| Tests Performed | 249 |
| Plugins Enabled | 1 |

### Observations

The initial assessment did not identify any critical warnings.

The system presents a reasonably secure default configuration for a clean Ubuntu 26.04.1 LTS installation. However, Lynis identified multiple opportunities for improvement related to hardening, monitoring, auditing, file integrity, and service management.

---

## Detected Security Components

| Component | Status |
|-----------|-----------|
| Firewall | Not Detected |
| Intrusion Detection Software | Not Detected |
| Malware Scanner | Not Detected |

---

## Findings Summary

The initial Lynis assessment identified 39 security recommendations distributed across multiple security domains.

The recommendations primarily affect:

- Package management and system maintenance.
- Authentication and password policies.
- Service and system configuration.
- Auditing and monitoring capabilities.
- File integrity monitoring.
- Network and firewall configuration.
- System hardening controls.
- Kernel and operating system security settings.

No critical warnings were detected during the assessment. However, several recommendations were identified that could improve the overall security posture of the system and increase the Hardening Index.

To support remediation planning, the findings were reviewed and classified according to their impact, complexity, and applicability within the scope of this laboratory environment.

---

## Findings Classification

### Quick Wins

The following recommendations can be implemented with minimal impact and are expected to provide an immediate security benefit.

| ID | Recommendation | Risk | Action |
|-----------|-----------|-----------|-----------|
| DEB-0831 | Install needrestart | Low | Implement |
| DEB-0880 | Install fail2ban | Medium | Implement |
| FIRE-4590 | Configure a firewall | Medium | Implement |
| ACCT-9622 | Enable process accounting | Medium | Implement |
| ACCT-9628 | Enable auditd | Medium | Implement |
| FINT-4350 | Install file integrity monitoring | Medium | Implement |
| PKGS-7370 | Install debsums | Low | Implement |
| PKGS-7394 | Install apt-show-versions | Low | Implement |

### Requires Analysis

The following recommendations require additional review before implementation due to their potential operational impact.

| ID | Recommendation | Risk | Action |
|-----------|-----------|-----------|-----------|
| BOOT-5122 | Protect GRUB with a password | Medium | Review |
| BOOT-5264 | Harden systemd services | Medium | Review |
| AUTH-9229 | Review PAM password hashing configuration | Medium | Review |
| AUTH-9230 | Configure password hashing rounds | Medium | Review |
| AUTH-9282 | Configure account expiration policies | Medium | Review |
| AUTH-9286 | Configure password aging policies | Medium | Review |
| AUTH-9328 | Harden default umask settings | Medium | Review |
| FILE-7524 | Restrict file permissions | Medium | Review |
| KRNL-6000 | Review sysctl configuration | High | Review |
| HRDN-7222 | Restrict compiler access | Medium | Review |
| HRDN-7230 | Deploy malware detection tooling | Medium | Review |
| PRNT-2307 | Restrict CUPS configuration access | Low | Review |

### Not Applicable

The following recommendations are considered outside the scope of this laboratory environment or would provide limited value for the project objectives.

| ID | Recommendation | Reason |
|-----------|-----------|-----------|
| FILE-6310 | Separate /home partition | Not required in temporary laboratory VM |
| FILE-6310 | Separate /var partition | Not required in temporary laboratory VM |
| USB-1000 | Disable USB storage support | USB functionality may be required during testing |
| LOGG-2154 | External logging server | No centralized logging infrastructure exists |
| NAME-4028 | Configure DNS domain name | Not relevant to standalone VM |
| TOOL-5002 | Automation tooling detection | Informational recommendation |
| NETW-3200 | Review DCCP protocol | Low priority for laboratory environment |
| NETW-3200 | Review SCTP protocol | Low priority for laboratory environment |
| NETW-3200 | Review RDS protocol | Low priority for laboratory environment |
| NETW-3200 | Review TIPC protocol | Low priority for laboratory environment |

### Pending Review

The remaining recommendations will be assessed during the implementation phase and evaluated individually to determine whether they should be implemented, deferred, or excluded from the project scope.

---

## Evidence

### Evidence 01 – Initial Audit Results

Screenshot of the Lynis final summary showing the baseline state of the system:

- Hardening Index: 63
- Warnings: 0
- Suggestions: 39

![Lynis initial audit results showing the baseline hardening index, warnings, and suggestions](images/Captura%20desde%202026-10-19%2022-49-52.png)

### Evidence 02 – Baseline Artifacts

Files generated during the initial audit:

- [artifacts/lynis-initial.log](artifacts/lynis-initial.log)
- [artifacts/lynis-report-initial.dat](artifacts/lynis-report-initial.dat)

These artifacts constitute the technical evidence used to document and validate the assessment results.

---

## Initial Conclusions

The baseline obtained provides an appropriate starting point for the hardening activities.

The results show a functional installation with no critical warnings and multiple recommendations aimed at improving the overall security posture of the system.

The next phase of the project will focus on analyzing and classifying the identified recommendations to determine which measures will be implemented and which do not apply to the laboratory environment defined for this project.