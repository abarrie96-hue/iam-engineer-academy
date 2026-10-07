# IAM-0002 — Mover Lifecycle Failure and Privilege Accumulation

## Ticket Information

| Field | Value |
|---|---|
| Ticket ID | IAM-0002 |
| Organization | ACME Financial (Simulated) |
| Category | Identity Lifecycle Management |
| Priority | High |
| Affected User | Michael Thompson |
| Status | Training Scenario — Proposed Resolution |

## Incident Description

Michael Thompson transferred from Engineering to Finance approximately 30 days ago.

His new Finance access was successfully provisioned, but he retained privileged access associated with his previous DevOps Engineer role.

### Previous Position

- Department: Engineering
- Role: DevOps Engineer

### Current Position

- Department: Finance
- Role: Financial Systems Analyst

## Current Access Review

| Entitlement | Assigned | Assessment |
|---|---|---|
| `Finance-Employees` | Yes | Required for current role |
| `Financial-Systems` | Yes | Required for current role |
| `DevOps-Engineers` | Yes | Requires removal review |
| `AWS-Production-Admin` | Yes | High-risk stale privilege |
| `Jenkins-Production` | Yes | Requires removal review |

## Initial Investigation

1. Verify Michael's identity and current employment information.
2. Confirm the department and role change in the authoritative HR system.
3. Review current group memberships, application assignments, and privileged entitlements.
4. Compare assigned access against the approved Finance access model.
5. Check for authorized exceptions or temporary business requirements.
6. Determine whether retained access violates IAM policies.

## Findings

- Michael's new Finance access was provisioned.
- Previous DevOps entitlements were not removed.
- Michael retained production administrative access beyond his current responsibilities.
- The manager confirmed Michael no longer performs DevOps work.
- No approved exception was identified.

## Root Cause

The Mover lifecycle process failed to revoke entitlements associated with Michael's previous role.

This resulted in **privilege accumulation**.

## Security Risks

- Excessive privileges
- Unauthorized production access
- Increased impact if the account is compromised
- Potential audit and compliance findings
- Violation of the Principle of Least Privilege

## Proposed Remediation

After confirming the required authorization:

1. Review the complete list of obsolete entitlements.
2. Remove Michael from `DevOps-Engineers`.
3. Revoke `AWS-Production-Admin` access.
4. Remove `Jenkins-Production` access.
5. Reevaluate any remaining direct or inherited DevOps permissions.
6. Confirm that required Finance access remains intact.
7. Document the changes and associated approvals.

## Validation Plan

Verify that Michael:

- Cannot assume or otherwise use the AWS production administrator role.
- Cannot access Jenkins Production through obsolete permissions.
- No longer inherits DevOps access.
- Can still access authorized Finance applications.

Review logs and entitlement records to confirm the changes.

**Lab status:** Proposed remediation; no live access changes performed.

## Preventive Improvements

- Automate Mover workflows using authoritative HR events.
- Perform entitlement reconciliation after department changes.
- Require periodic access reviews.
- Apply expiration dates to approved temporary access.
- Alert on stale privileged access.

## Lessons Learned

A successful Mover process must both provision appropriate new access and remove obsolete access.

Simply granting new permissions without reviewing existing entitlements creates security risk.

## Interview Talking Point

This scenario demonstrates how to investigate privilege accumulation, apply least privilege, validate entitlement removal, and document IAM remediation for audit purposes.