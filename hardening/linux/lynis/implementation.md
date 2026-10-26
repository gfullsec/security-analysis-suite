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

To be completed.

#### Evidence

To be added.

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

To be completed.

#### Evidence

To be added.

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
sudo apt install ufw -y

sudo ufw default deny incoming

sudo ufw default allow outgoing

sudo ufw enable
```

#### Validation

To be completed.

#### Evidence

To be added.

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

To be completed.

#### Evidence

To be added.

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
| IMPL-001 | DEB-0831 | Needrestart | Pending |
| IMPL-002 | DEB-0880 | Fail2ban | Pending |
| IMPL-003 | FIRE-4590 | UFW Firewall | Pending |
| IMPL-004 | ACCT-9622 | Process Accounting | Pending |
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