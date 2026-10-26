# Linux Hardening Project with Lynis

## Overview

This project documents the assessment and hardening of a clean Ubuntu 26.04.1 LTS installation using Lynis as the primary security auditing tool.

The objective is to identify security configuration weaknesses, analyze security recommendations, and implement hardening measures in a controlled and documented manner. The project follows a baseline, assessment, remediation, and validation methodology.

---

## Objectives

- Perform an initial security assessment using Lynis.
- Establish a security baseline for the system.
- Analyze findings and security recommendations.
- Classify hardening measures according to risk and impact.
- Implement selected security improvements.
- Validate implemented changes through a follow-up audit.
- Document the entire process in a reproducible manner.

---

## Environment

### Operating System

- Ubuntu 26.04.1 LTS Desktop

### Platform

- Oracle VirtualBox 7.2.20

### Virtual Machine

- Name: `hardening-ubuntu`
- Memory: 4 GB
- CPU: 2 vCPU
- Disk: 40 GB Dynamic VDI

- Machine documentation: [Ubuntu hardening procedure](https://github.com/gfullsec/security-analysis-suite/tree/main/lab-documentation/procedures/ubuntu-26.04.01-lts/hardening-ubuntu)


---

## Methodology

The project is structured around the following phases:

1. Initial Assessment
2. Baseline Establishment
3. Findings Analysis
4. Hardening Implementation
5. Post-Remediation Assessment
6. Validation and Verification
7. Documentation and Conclusions

---

## Documentation

| Document | Description |
|-----------|-----------|
| assessment.md | Initial assessment, baseline audit, and findings analysis |
| implementation.md | Applied hardening measures and technical justification |
| validation.md | Final validation, reassessment, and results comparison |

---

## Initial Security Baseline

Results obtained from the initial Lynis assessment:

- Hardening Index: 63
- Warnings: 0
- Suggestions: 39
- Tests Performed: 249

These results provide the baseline used to measure the effectiveness of the hardening measures applied during the project.

---

## Expected Outcome

Upon completion of the project, the following outcomes are expected:

- Increased Hardening Index.
- Reduced number of outstanding recommendations.
- Improved system security configuration.
- A documented and reproducible Ubuntu 26.04 LTS hardening process.