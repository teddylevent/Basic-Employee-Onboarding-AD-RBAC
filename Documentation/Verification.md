# Verification Record

**Review date:** September 18, 2026

**Environment:** `NMG-DC01` in UTM

**Method:** Read the original daily notes and inspect the running directory through read-only PowerShell queries.

## Observed Results

| Check | Observed result |
| --- | --- |
| Domain | `NMG.com`, NetBIOS name `NMG` |
| Operating system | Microsoft Windows Server 2025 Standard |
| Lab IPv4 address | `192.168.64.5`, prefix origin `Manual` |
| Employee inventory | 15 named lab employees, separate from built-in accounts |
| Account attributes | Names, usernames, UPNs, departments, and titles match the published inventory |
| OU placement | Each of the 15 employees is in the matching department OU |
| Departmental membership | Each employee has the expected departmental group in the inspected `MemberOf` attribute |
| Group configuration | Four department groups; each is Global / Security |
| Jane Cooper | HR OU, `HR-Users`, HR Payroll Specialist, department HR |
| Jane's manager | Sandra Torres in the HR OU |
| GPO inventory | `Default Domain Policy` and `Default Domain Controllers Policy` only |

## Queries Used

These are read-only inspections. The published results summarize the output reviewed in the VM; they are not a raw log export.

```powershell
$u = Get-ADUser -Filter * -Properties Title,Department,MemberOf

$u | Sort-Object Name |
    Format-Table Name,SamAccountName,UserPrincipalName,Department,Title -AutoSize

$u | Where-Object Department | Sort-Object SamAccountName |
    Format-Table SamAccountName,DistinguishedName,MemberOf -Wrap

Get-ADGroup -Filter "Name -like '*-Users'" |
    Format-Table Name,GroupScope,GroupCategory

Get-ADDomain | Format-Table DNSRoot,NetBIOSName
Get-NetIPAddress -AddressFamily IPv4 | Format-Table IPAddress,PrefixOrigin
Get-CimInstance Win32_OperatingSystem | Format-Table Caption
Get-ADUser jcooper -Properties Manager | Format-Table Manager
Get-GPO -All | Format-Table DisplayName
```

## Evidence Boundaries

The original notes and retained local screenshots document the work across Days 1–4. The Day 5 queries independently confirm the final directory configuration. The support ticket is a simulation, and the original resolution's statement about successful resource access after sign-in is a reported outcome, not an independently reproduced application test.

No departmental GPO was found in the GPO inventory. Resource ACLs, mapped drives, payroll or HR applications, workstation resultant policy, and successful or denied share access were not verified. Moving Jane's user object does not establish that her computer's policies changed. No claim of production readiness or HIPAA compliance is made.

Screenshots and course materials remain outside this repository. Passwords, tokens, and other authentication material are excluded.
