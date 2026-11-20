# IAM-0008 — Microsoft Entra ID Privileged Access Review

**Organization:** ACME Corporation  
**Category:** Identity & Access Management  
**Priority:** Medium  
**Status:** Closed  
**Environment:** Microsoft Entra ID

## 1. Business Request

The Security Team requested an access review to verify that standard employees and departmental security groups do not have unnecessary administrative privileges in Microsoft Entra ID.

## 2. Scope

- User: Jennifer Smith
- Department: Finance
- Security Group: `SG-Finance-Users`
- Administrative Role: Global Administrator

## 3. Audit Checklist

- [x] Verified Jennifer Smith's Entra ID account.
- [x] Confirmed Jennifer has no administrative roles assigned.
- [x] Verified Jennifer belongs to `SG-Finance-Users`.
- [x] Confirmed Jennifer is not a Finance group owner.
- [x] Reviewed Global Administrator assignments.
- [x] Confirmed neither Jennifer nor `SG-Finance-Users` has Global Administrator access.

## 4. Findings

**Finding 1 — Standard User Privileges**

Jennifer Smith has no Entra administrative roles assigned.

**Finding 2 — Group Membership**

Jennifer is a member of `SG-Finance-Users` and is not a group owner.

**Finding 3 — Privileged Access**

Neither Jennifer nor the Finance security group has Global Administrator access.

## 5. Security Assessment

No excessive administrative privileges were identified within the reviewed scope.

The configuration aligns with the Principle of Least Privilege.

## 6. Remediation

No remediation required for the reviewed access assignments.

## 7. Verification

Verification was performed through the Microsoft Entra admin center by reviewing user roles, group membership, group ownership, and Global Administrator assignments.

## 8. Final Status

**Closed — Access review completed. No remediation required.**