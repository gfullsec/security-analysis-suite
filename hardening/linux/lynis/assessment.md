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

The recommendations provided by Lynis are primarily distributed across the following categories:

- Package management.
- Account and password management.
- Service configuration.
- Auditing and monitoring.
- File integrity.
- Network security.
- System hardening.
- Kernel configuration.

A detailed classification of the findings will be performed during the analysis phase and will serve as the basis for selecting the hardening measures to be implemented.

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