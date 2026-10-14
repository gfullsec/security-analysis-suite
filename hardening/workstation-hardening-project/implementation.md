# Implementation

## 1. Project Overview

This document records the practical implementation of the workstation migration project.

The objective was to replace Windows 10 as the primary operating system with Ubuntu 26.04 LTS while preserving access to legacy software through virtualization.

Implementation activities included:

- Ubuntu deployment.
- Data migration.
- Recovery of the legacy Windows environment.
- Virtualization platform configuration.
- Storage redesign.
- Security baseline implementation.

---

## 2. Environment Preparation

Prior to migration, the existing Windows environment was analyzed and backed up.

Activities completed:

- Identification of hardware compatibility requirements.
- Preservation of user data.
- Backup of the existing Windows installation.
- Validation of available storage devices.
- Creation of project documentation repository.

---

## 3. Ubuntu Deployment

Ubuntu 26.04 LTS was installed as the primary operating system.

Post-installation activities included:

- Operating system updates.
- User account configuration.
- Storage configuration.
- Software installation.
- Project workspace preparation.

The system was successfully validated as the primary daily-use environment.

---

## 4. Data Migration

User documents and project files were migrated from the previous Windows environment.

Activities completed:

- Transfer of existing data.
- Validation of file accessibility.
- Organization of user directories.
- Verification of storage availability.

All required user data remained accessible after migration.

---

## 5. Legacy Environment Recovery

A legacy Windows 10 installation was preserved through virtualization.

Implementation included:

- Extraction of the original Windows installation image.
- Conversion from VHD to VDI format.
- Deployment within VirtualBox.
- Configuration of storage and virtual hardware.
- Validation of application functionality.

The recovered environment successfully booted and remained operational.

---

## 6. Legacy Application Validation

The following applications were validated within the virtualized environment:

- Adobe Photoshop
- Adobe Illustrator
- Adobe InDesign

Additional testing included:

- Installation of printer drivers.
- Guest Additions deployment.
- Shared folder configuration.
- Storage performance evaluation.

All required applications remained functional after migration.

---

## 7. Deviation 1: SSD Capacity Constraints

### Description

A recovered 120 GB SSD was initially designated as the storage location for the virtualized Windows environment.

During implementation it became clear that the available capacity would provide limited long-term headroom for a legacy virtual machine expected to grow over time.

### Impact

Potential consequences included:

- Limited future growth.
- Reduced snapshot capacity.
- Increased storage management complexity.

### Resolution

The storage design was reviewed and alternative deployment options were assessed before committing to the final virtualization strategy.

### Lessons Learned

Capacity planning should consider not only current usage but also future growth, snapshot requirements, and maintenance activities.

---

## 8. Deviation 2: Legacy Virtual Disk Capacity

### Description

After converting the original Windows installation from VHD to VDI format, an unexpected storage design issue was identified.

Although the converted virtual disk occupied approximately 76 GB on physical storage, analysis revealed that the image had inherited the logical capacity of the original physical device.

```text
Virtual Capacity: ~930 GB
Physical Size:    ~76 GB
SSD Capacity:     ~110 GB usable
```

This meant that the virtual machine could continue expanding despite appearing relatively small on disk.

### Impact

Potential risks included:

- SSD capacity exhaustion.
- Virtual machine instability.
- Virtual disk corruption caused by lack of available storage.
- Additional maintenance complexity.

### Assessment

Several alternatives were evaluated:

1. Reduce the virtual disk capacity manually.
2. Rebuild the Windows environment from scratch.
3. Relocate the legacy virtual machine to secondary storage.

The first option introduced unnecessary complexity and risk.

The second option required full operating system and application reinstallation.

### Resolution

A backup copy of the virtual disk was created and tested on the secondary 1 TB storage device.

Performance testing demonstrated that the intended workload:

- Adobe Photoshop
- Adobe Illustrator
- Adobe InDesign

remained fully usable despite the performance limitations of mechanical storage.

The virtual machine was retained on secondary storage while the dedicated SSD was reserved for future virtualization activities and a cleaner long-term deployment strategy.

### Lessons Learned

Virtual disk assessment should always include both:

- Physical disk consumption.
- Maximum virtual capacity.

A virtual machine may appear relatively small while still retaining the growth characteristics of the original source device.

---

## 9. Virtual Machine Optimization

Several optimizations were applied to improve guest usability and integration.

Implemented improvements included:

- Guest Additions installation.
- Shared folder configuration.
- Dynamic display support.
- Resource allocation tuning.
- Storage location optimization.

These changes significantly improved the usability of the virtualized environment.

---

## 10. Final State

The project successfully achieved its primary objectives.

Final architecture:

```text
                           INTERNET
                               │
                               ▼
                      Ubuntu 26.04 LTS
                         Primary Host
                               │
     ┌─────────────────────────┼─────────────────────────┐
     │                         │                         │
     ▼                         ▼                         ▼
  Firefox               Development               Security Tooling
                           Tools
                               │
                               ▼
                         VirtualBox
                               │
                               ▼
                        Windows 10 VM
                           (Legacy)
                               │
                 ┌─────────────┼─────────────┐
                 ▼             ▼             ▼
            Photoshop     Illustrator     InDesign
```

Key outcomes:

- Ubuntu 26.04 LTS deployed as primary operating system.
- User data successfully migrated.
- Legacy Windows environment preserved.
- Adobe application compatibility maintained.
- Guest integration implemented.
- Shared workspace functionality validated.
- Long-term migration path established.

---

## 11. Evidence

### Evidence 1: Ubuntu 26.04 LTS Host Deployment

The Ubuntu host was successfully deployed and configured as the primary operating environment.

![Ubuntu 26.04 LTS Host Deployment](./images/implementation/Captura%20desde%202026-10-14%2013-39-55.png)

![Ubuntu 26.04 LTS Host Deployment](./images/implementation/Captura%20desde%202026-10-14%2013-02-54.png)

---

### Evidence 2: Dedicated Virtualization Storage

A dedicated SSD was prepared and mounted for virtualization activities.

![Dedicated Virtualization Storage 1](./images/implementation/Captura%20desde%202026-10-14%2013-38-47.png)
![Dedicated Virtualization Storage 2](./images/implementation/Captura%20desde%202026-10-14%2013-39-00.png)
![Dedicated Virtualization Storage 3](./images/implementation/Captura%20desde%202026-10-14%2013-38-55.png)

---

### Evidence 3: Legacy Disk Conversion

The original Windows installation was successfully extracted to VHD format

![Legacy Disk Conversion](./images/implementation/Captura%20de%20pantalla%202026-10-07%20205332.png)

![Legacy Disk Conversion](./images/implementation/Captura%20de%20pantalla%202026-10-07%20205451.png)

![Legacy Disk Conversion](./images/implementation/Captura%20de%20pantalla%202026-10-07%20210743.png)

---

### Evidence 4: VirtualBox Configuration tested into another machine

VirtualBox was configured to host the recovered Windows environment.

![VirtualBox Configuration](./images/implementation/Captura%20desde%202026-10-14%2012-21-04.png)

---

### Evidence 5: Windows 10 Recovery tested into another machine

The recovered Windows environment successfully booted as a virtual machine.

![Windows 10 Recovery tested into another machine](./images/implementation/Captura%20desde%202026-10-14%2012-24-31.png)

---

### Evidence 6: Windows 10 Clean Running

The recovered Windows environment successfully booted as a virtual machine.

![Windows 10 Clean Running](./images/implementation/Captura%20desde%202026-10-14%2013-01-04.png)

---


### Evidence 7: Shared Folder Integration

Shared folders were configured between host and guest systems.

![Shared Folder Integration](./images/implementation/Captura%20desde%202026-10-14%2012-46-39.png)

![Shared Folder Integration](./images/implementation/Captura%20desde%202026-10-14%2012-59-53.png)

---

### Evidence 8: Legacy Application Validation

The required legacy applications were successfully validated.

![Legacy Application Validation 1](./images/implementation/Captura%20desde%202026-10-14%2012-55-46.png)
![Legacy Application Validation 2](./images/implementation/Captura%20desde%202026-10-14%2012-55-16.png)
![Legacy Application Validation 3](./images/implementation/Captura%20desde%202026-10-14%2012-54-34.png)

---

### Evidence 9: Snapshot and Backup Strategy

A recovery strategy was implemented to preserve the operational state of the legacy environment.

![Snapshot and Backup Strategy](./images/implementation/Captura%20desde%202026-10-14%2012-44-52.png)

---

### Evidence 10: Final Operational Environment

The final solution operates according to the target architecture.

![Final Operational Environment](./images/implementation/Captura%20desde%202026-10-14%2013-50-33.png)

---


## 12. Conclusion

The migration successfully transitioned the workstation from a Windows-centric environment to an Ubuntu-based operating model while preserving compatibility with required legacy software.

The implementation process identified several storage-related challenges that required architectural adjustments and additional evaluation. These issues were successfully resolved and provided practical experience in virtualization, storage planning, migration strategy, and operational decision-making.

The resulting platform provides a maintainable Linux-based workstation while retaining access to critical legacy applications through an isolated and controlled virtualized environment. The final solution establishes a solid foundation for future hardening activities, cybersecurity experimentation, and continued platform modernization.
``