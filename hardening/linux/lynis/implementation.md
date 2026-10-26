# Hardening Implementation

## Overview

This document records the security hardening measures implemented on the Ubuntu 26.04.1 LTS assessment system following the findings identified during the initial Lynis audit.

The objective of this phase is to implement selected security improvements, reduce the number of outstanding recommendations, and increase the overall Hardening Index while maintaining system stability and functionality.

---

## Implementation Scope

The measures implemented in this phase were selected from the findings classified as Quick Wins during the assessment process.

These recommendations were prioritized because they provide immediate security benefits with minimal operational impact.

---

## Implemented Measures

### IMPL-001 – Needrestart Installation

#### Related Finding

```text
DEB-0831
Install needrestart
```

#### Objective

Identify services using outdated libraries after package upgrades and determine when service restarts are required.

#### Implementation

```bash
sudo apt install needrestart -y
```

#### Validation

The package was successfully installed and configured.

Needrestart is now available to identify services requiring a restart after software updates and package upgrades.

#### Evidence

![Needrestart installation](images/needrestart-installation.png)

---

### IMPL-002 – Fail2ban Installation

#### Related Finding

```text
DEB-0880
Install fail2ban
```

#### Objective

Automatically detect and block repeated authentication failures.

#### Implementation

```bash
sudo apt install fail2ban -y
```

#### Validation

Fail2ban was successfully installed and the service started automatically after installation.

The service was verified as active and enabled through systemd.

#### Evidence

##### Evidence 01 – Fail2ban Installation

The package was successfully installed together with the required dependencies.

![Fail2ban installation](images/fail2ban-installation.png)

##### Evidence 02 – Service Status Verification

The Fail2ban service was verified as active and running after installation.

![Fail2ban service status](images/fail2ban-service-status.png)

---

### IMPL-003 – Firewall Configuration

#### Related Finding

```text
FIRE-4590
Configure a firewall/packet filter
```

#### Objective

Control incoming and outgoing network traffic according to defined security rules.

#### Implementation

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable
```

#### Validation

UFW was configured with a default deny policy for inbound traffic and a default allow policy for outbound traffic.

The firewall was successfully enabled and verified using the UFW status command.

#### Evidence

##### Evidence 01 – Baseline Firewall Status

The firewall was installed but inactive before configuration.

![UFW inactive status](images/ufw-baseline-status.png)

##### Evidence 02 – Firewall Configuration and Activation

The firewall was configured and enabled using secure default policies.

![UFW enabled status](images/ufw-enabled-status.png)

---

### IMPL-004 – Process Accounting

#### Related Finding

```text
ACCT-9622
Enable process accounting
```

#### Objective

Record executed commands and process activity to improve accountability and forensic capabilities.

#### Implementation

```bash
sudo apt install acct -y
```

#### Validation

Process accounting was successfully installed and enabled.

The accounting service was verified through systemd and confirmed as active after installation.

#### Evidence

##### Evidence 01 – Process Accounting Installation and Validation

The accounting package was installed successfully and the service was verified after deployment.

![Process Accounting Installation and Validation](images/acct-installation-and-validation.png)

---

### IMPL-005 – Auditd Enablement

#### Related Finding

```text
ACCT-9628
Enable auditd to collect audit information
```

#### Objective

Enable Linux auditing capabilities and event collection for security monitoring and investigation purposes.

#### Implementation

```bash
sudo apt install auditd -y
```

#### Validation

To be completed.

#### Evidence

To be added.

---

### IMPL-006 – File Integrity Monitoring

#### Related Finding

```text
FINT-4350
Install a file integrity tool
```

#### Objective

Monitor critical system files and detect unauthorized modifications.

#### Implementation

```bash
sudo apt install aide -y
```

#### Validation

To be completed.

#### Evidence

To be added.

---

### IMPL-007 – Package Verification Utility

#### Related Finding

```text
PKGS-7370
Install debsums
```

#### Objective

Provide package integrity verification based on package checksums.

#### Implementation

```bash
sudo apt install debsums -y
```

#### Validation

To be completed.

#### Evidence

To be added.

---

### IMPL-008 – Package Version Review Utility

#### Related Finding

```text
PKGS-7394
Install apt-show-versions
```

#### Objective

Improve package management visibility and patch tracking.

#### Implementation

```bash
sudo apt install apt-show-versions -y
```

#### Validation

To be completed.

#### Evidence

To be added.

---

## Implementation Summary

| ID | Related Finding | Measure | Status |
|-----------|-----------|-----------|-----------|
| IMPL-001 | DEB-0831 | Needrestart | Implemented |
| IMPL-002 | DEB-0880 | Fail2ban | Implemented |
| IMPL-003 | FIRE-4590 | UFW Firewall | Implemented |
| IMPL-004 | ACCT-9622 | Process Accounting | Implemented |
| IMPL-005 | ACCT-9628 | Auditd | Pending |
| IMPL-006 | FINT-4350 | AIDE | Pending |
| IMPL-007 | PKGS-7370 | Debsums | Pending |
| IMPL-008 | PKGS-7394 | Apt-show-versions | Pending |

---

## Expected Outcome

The implementation phase is expected to:

- Improve the Hardening Index.
- Increase auditing and monitoring capabilities.
- Improve system visibility and accountability.
- Add file integrity monitoring.
- Introduce basic intrusion prevention capabilities.
- Provide a baseline host firewall configuration.

Results will be validated during the post-hardening assessment phase.