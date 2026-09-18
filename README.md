# Basic Employee Onboarding (AD)(RBAC)

An Active Directory and identity access management lab for **Northstar Medical Group**, a fictional healthcare organization.

**15 employee accounts · 4 departments · 4 security groups · 1 resolved identity configuration incident**

Built in UTM on Windows Server 2025 Standard. Lab work completed September 14–17, 2026; portfolio and directory verification completed September 18, 2026.

## Problem Statement

The fictional Northstar Medical Group inherited disorganized identity administration from its managed service provider (MSP). Manual onboarding, inconsistent account attributes, and missing departmental structure made access assignments difficult to maintain and review. In a healthcare setting, that scenario creates concerns about inappropriate access to sensitive information and HIPAA-related risk. This lab models the identity configuration work needed to address those problems; it does not represent a production healthcare deployment or a compliance assessment.

## Solution Overview

I built the `NMG.com` domain on the `NMG-DC01` domain controller and organized employee accounts into Finance, HR, IT, and Operations OUs. I created one global security group per department to establish a simple, flat RBAC model. I provisioned 15 fictional employee identities using consistent usernames, UPNs, departments, and job titles. I investigated ticket `NMG-0047` and corrected Jane Cooper's OU placement, departmental group membership, and HR profile attributes. The resulting directory provides a consistent foundation for assigning resource permissions through groups, with the configuration and verification documented in this repository.

## Start Here

- [RBAC structure and final group memberships](Documentation/RBAC-Structure.md)
- [Complete employee inventory](Documentation/User%20List%20Documentation.md)
- [NMG-0047 incident resolution](Incident-Reports/NMG-0047-Resolution.txt)
- [Verification results and limits](Documentation/Verification.md)

## Directory Structure

```text
NMG.com
├── Finance     → Finance-Users     → 4 employees
├── HR          → HR-Users          → 4 employees, including Jane Cooper
├── IT          → IT-Users          → 4 employees
└── Operations  → Operations-Users  → 3 employees
```

The arrows show the department-to-group mapping. OU placement and group membership are configured separately.

## Incident: Jane Cooper's HR Access

The simulated support ticket reported that Jane could sign in but could not access HR resources, and her desktop environment differed from her HR teammates. Investigation showed her account in the Operations OU and `Operations-Users`, despite her role as an HR Payroll Specialist. I moved her account to HR, removed `Operations-Users`, added `HR-Users`, and updated her job title, department, and manager.

The final directory state was independently checked on September 18: Jane is in `OU=HR,DC=NMG,DC=com`, belongs to `HR-Users`, and reports to Sandra Torres. The original resolution notes record successful access after a restart and sign-in. The evidence verified for this portfolio establishes the directory corrections; application access, share permissions, and resulting desktop policies were not independently tested.

## Tools Used

| Tool or method | Use in this project |
| --- | --- |
| Windows Server 2025 Standard | Domain controller operating system |
| Active Directory Domain Services | Domain, employee identities, OUs, and security groups |
| Active Directory Users and Computers | Account provisioning and incident remediation |
| UTM on macOS | Virtual machine hosting |
| Windows PowerShell / Active Directory module | Read-only verification of the completed directory |
| Group Policy | OU scope concepts and inspection of existing GPOs |
| RBAC | Departmental role and group design |
| Git and GitHub | Versioned portfolio documentation |

## Project Timeline

| Phase | Completed | Result |
| --- | --- | --- |
| Day 1 — Domain setup | September 14, 2026 | Created `NMG.com`, promoted `NMG-DC01`, and configured the lab's static address |
| Day 2 — Directory organization | September 14, 2026 | Created four departmental OUs and four security groups |
| Day 3 — User provisioning | September 15, 2026 | Created 15 accounts and assigned departmental memberships |
| Day 4 — Incident response | September 17, 2026 | Corrected Jane Cooper's identity configuration for ticket `NMG-0047` |
| Day 5 — Portfolio packaging | September 18, 2026 | Verified the current directory and organized the case study for GitHub |

## Key Accomplishments

- Built a working lab domain with a dedicated domain controller.
- Established a clear four-department OU and security group structure.
- Provisioned and documented all 15 employee identities.
- Resolved both the incorrect OU placement and incorrect departmental membership in the Jane Cooper scenario.
- Reconciled the original Day 3 roster with the corrected Day 4 state: HR increased from three to four users, and Operations decreased from four to three.
- Verified account attributes, OU placement, and departmental memberships directly in the running VM.

## What the Lab Demonstrates

The implemented scope is directory organization, user provisioning, departmental group membership, and identity troubleshooting. Group membership only grants access where permissions have been assigned to that group. Group Policy scope depends on GPO links and filtering as well as OU placement. See [Microsoft's security group documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups) and [Group Policy scope documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-scope).

The verification found only the two default GPOs. Departmental resource ACLs, applications, drive mappings, and custom department GPOs are not demonstrated here. `IT-Users` is a departmental group and does not, by its name alone, confer Domain Admin privileges.

## Repository Structure

```text
Documentation/
  Domain Config File.md       Domain setup and completion date
  Security Group Doc.md       OU purposes and group configuration
  User List Documentation.md  All 15 identities and final assignments
  RBAC-Structure.md           Department-to-group access model
  Verification.md             Read-only checks and evidence boundaries
Incident-Reports/
  NMG-0047-Resolution.txt      Investigation, changes, and verification
Screenshots/
  README.md                   Explains why images are excluded
```

## Video Walkthrough

**Walkthrough link: coming soon.** The video has not been recorded or published yet.

## Publication Scope

This repository contains original documentation of a fictional lab. Screenshots, course PDFs, internal lesson/checklist text, and credentials are excluded. The `Screenshots` folder is retained as a documentation placeholder only.
