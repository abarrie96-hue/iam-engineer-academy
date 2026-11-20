# IAM-0009 — Microsoft Entra ID Identity Lifecycle Management

**Organization:** ACME Corporation  
**Category:** Identity & Access Management  
**Priority:** High  
**Environment:** Microsoft Entra ID  
**Status:** Closed

## 1. Business Request

The HR department requested that the IAM team manage Jennifer Smith's identity throughout the Joiner, Mover, and Leaver lifecycle.

The objective was to ensure appropriate access was provisioned, updated, and removed as Jennifer's employment status and job responsibilities changed.

## 2. Identity Information

- **Employee:** Jennifer Smith
- **Company:** ACME Corporation
- **Initial Department:** Finance
- **Initial Job Title:** Financial Analyst
- **Transferred Department:** Human Resources
- **Transferred Job Title:** HR Specialist
- **Final Account Status:** Disabled

## 3. Joiner Workflow

**Actions Completed:**

- [x] Created Jennifer Smith's Microsoft Entra ID account during Day 8.
- [x] Verified user profile information.
- [x] Confirmed the account was enabled.
- [x] Created `SG-Finance-Users`.
- [x] Assigned Jennifer to the Finance security group.
- [x] Verified Jennifer had no administrative roles.

**Result:** Identity provisioned with the intended departmental group membership.

## 4. Mover Workflow

**Business Scenario:** Jennifer transferred from Finance to Human Resources.

**Actions Completed:**

- [x] Updated department to Human Resources.
- [x] Updated job title to HR Specialist.
- [x] Removed Jennifer from `SG-Finance-Users`.
- [x] Created `SG-HR-Users`.
- [x] Added Jennifer to `SG-HR-Users`.
- [x] Verified the updated group memberships.

**Result:** Departmental group membership was updated to reflect Jennifer's new responsibilities.

## 5. Leaver Workflow

**Business Scenario:** Jennifer's employment ended in the simulated ACME environment.

**Actions Completed:**

- [x] Disabled Jennifer's Microsoft Entra ID account.
- [x] Requested revocation of sign-in sessions.
- [x] Removed Jennifer from `SG-HR-Users`.
- [x] Verified Finance group membership was already removed.
- [x] Confirmed the account remained disabled.
- [x] Preserved the account rather than deleting it.

**Result:** The account was disabled and the reviewed departmental group memberships were removed.

## 6. Security Controls

The following IAM principles were applied:

**Least Privilege:** Access was limited to the departmental group memberships required for the simulated job assignments.

**Role-Based Access Control:** Microsoft Entra security groups were used to organize departmental membership.

**Access Lifecycle Management:** Identity attributes and group memberships were updated during the employee's lifecycle.

**Session Revocation:** Microsoft Entra session revocation was requested during offboarding.

**Auditability:** Changes and verification results were documented for review.

## 7. Final Verification

| Control | Result |
|---|---|
| Account disabled | Verified |
| Session revocation requested | Verified |
| Finance group membership | Removed |
| HR group membership | Removed |
| Account preserved | Verified |
| Application-specific access and sessions | Not tested |

## 8. Findings

No unexpected departmental group memberships were identified in the reviewed scope after offboarding.

Application-specific permissions, direct assignments, and third-party sessions were not independently tested.

## 9. Remediation

The simulated employee's departmental group memberships were removed, sign-in was disabled, and session revocation was requested.

No additional remediation was identified within the tested scope.

## 10. Final Status

**Status:** Closed

**Resolution:** Joiner, Mover, and Leaver workflows
completed successfully in Microsoft Entra ID.

**Security Verification:**
- Account disabled.
- Sign-in session revocation requested.
- Finance group membership removed.
- HR group membership removed.
- Account preserved for auditing.

**Limitations:** Application-specific access and
third-party sessions were not independently tested.

**Ticket Resolution:** Completed within the
defined lab scope.