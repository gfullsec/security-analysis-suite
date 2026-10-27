# Windows 11 Hardening Project

## Overview

This project documents the assessment and hardening of a clean Windows 11 Pro installation using native Microsoft security controls, local security policies, auditing capabilities, and security best practices.

The objective is to identify security configuration weaknesses, analyze security recommendations, and implement hardening measures in a controlled and documented manner. The project follows a baseline, assessment, remediation, and validation methodology.

## Objectives

- Perform an initial security assessment.
- Establish a security baseline for the system.
- Analyze findings and security recommendations.
- Classify hardening measures according to risk and impact.
- Implement selected security improvements.
- Validate implemented changes through a follow-up assessment.
- Document the entire process in a reproducible manner.

## Environment

### Operating System

- Windows 11 Pro 26H2
- Build 26300.9457

### Platform

- Oracle VirtualBox

### Virtual Machine

- Name: hardening-win11
- Memory: 8 GB
- CPU: 2 vCPU
- Disk: 80 GB Dynamic VDI
- TPM: 2.0
- Secure Boot: Enabled
- Machine documentation: [Windows 11 VM Creation](https://github.com/gfullsec/security-analysis-suite/blob/main/lab-documentation/procedures/windows-11-pro/hardening-win11/vm-creation.md)

## Methodology

The project is structured around the following phases:

- Initial Assessment
- Baseline Establishment
- Findings Analysis
- Hardening Implementation
- Post-Remediation Assessment
- Validation and Verification
- Documentation and Conclusions

## Documentation

| Document | Description |
|-----------|-----------|
| assessment.md | Initial assessment, baseline audit, and findings analysis |
| implementation.md | Applied hardening measures and technical justification |
| validation.md | Final validation, reassessment, and results comparison |

## Initial Security Baseline

The initial assessment will be performed against a fully updated Windows 11 Pro installation before any hardening measures are applied.

The baseline assessment results will be used as the reference point for measuring the effectiveness of the implemented security controls.

## Expected Outcome

Upon completion of the project, the following outcomes are expected:

- Improved Windows security configuration.
- Reduced attack surface.
- Enhanced auditing and monitoring capabilities.
- Strengthened authentication and system security settings.
- A documented and reproducible Windows 11 hardening process.