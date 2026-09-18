# Basic Employee Onboarding (AD)(RBAC)

An Active Directory and identity access management lab for **Northstar Medical Group**, a fictional healthcare organization.

**15 employee accounts · 4 departments · 4 security groups · 1 resolved identity configuration incident**


## Problem Statement

The fictional Northstar Medical Group inherited disorganized identity administration from its managed service provider (MSP). Manual onboarding, inconsistent account attributes, and missing departmental structure made access assignments difficult to maintain and review. In a healthcare setting, that scenario creates concerns about inappropriate access to sensitive information and HIPAA-related risk. This lab models the identity configuration work needed to address those problems.

## Solution Overview

I built the `NMG.com` domain on the `NMG-DC01` domain controller and organized employee accounts into Finance, HR, IT, and Operations OUs. I created one global security group per department to establish a simple, flat RBAC model. I provisioned 15 fictional employee identities using consistent usernames, UPNs, departments, and job titles. I investigated ticket `NMG-0047` and corrected Jane Cooper's OU placement, departmental group membership, and HR profile attributes. The directory provides a consistent foundation for assigning resource permissions through groups.


## Tools Used

| Tool or method | Use in this project |
| --- | --- |
| Windows Server 2025 Standard | Domain controller operating system |
| Active Directory Domain Services | Domain, employee identities, OUs, and security groups |
| Active Directory Users and Computers | Account provisioning and incident remediation |
| UTM on macOS | Virtual machine |
| Group Policy | OU scope concepts and inspection of existing GPOs |
| RBAC | Departmental role and group design |

## Project Timeline

| Phase | Completed | Result |
| --- | --- | --- |
| Day 1 — Domain setup | September 14, 2026 | Created `NMG.com`, promoted `NMG-DC01`, and configured the lab's static address |
| Day 2 — Directory organization | September 14, 2026 | Created four departmental OUs and four security groups |
| Day 3 — User provisioning | September 15, 2026 | Created 15 accounts and assigned departmental memberships |
| Day 4 — Incident response | September 17, 2026 | Corrected Jane Cooper's identity configuration for ticket `NMG-0047` |


## Key Accomplishments

- Built a working lab domain with a dedicated domain controller.
- Established a four-department OU and security group structure.
- Provisioned and documented all 15 employee identities.
- Resolved both the incorrect OU placement and incorrect department membership in the Jane Cooper scenario.
- Verified account attributes, OU placement, and departmental memberships directly in the running VM.


## Video Walkthrough

[Watch the lab walkthrough on YouTube](https://youtu.be/rl8FhI2mtS4)



## What I Would Do Differently in Production



1. Onboarding should be automated with scripting, not manually entered. A script that uses the department as an input to automatically determine the correct OU, user attributes, and group memberships would prevent users from being placed in the wrong OU.
   
2. Having a single domain controller equals a single point of failure. A second domain controller would provide redundancy.
