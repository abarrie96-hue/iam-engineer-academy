# IAM-0003 — Separation of Duties Access Conflict

## Ticket Information

| Field | Value |
|---|---|
| Ticket ID | IAM-0003 |
| Organization | ACME Financial (Simulated) |
| Category | Access Governance / Separation of Duties |
| Priority | High |
| Affected User | Robert Miller |
| Department | Finance — Accounts Payable |
| Status | Training Scenario — Proposed Resolution |

## Incident Description

Robert Miller, an Accounts Payable Specialist, requests permission to approve vendor payments.

His manager is on vacation, and the Finance department needs to continue processing payments.

Robert already has permissions to create vendors and initiate payments.

## Existing Access

| Entitlement | Status |
|---|---|
| Create Vendor | Assigned |
| Create Payment | Assigned |
| Approve Vendor Payments | Requested |

## Security Concern

Granting the requested entitlement would potentially violate Separation of Duties (SoD).

Robert could both initiate and approve payments, eliminating an important independent control.

### Toxic Access Combination

`Create Payment` + `Approve Payment`

This combination can create fraud and financial-control risks.

## Initial Investigation

1. Verify Robert's identity and current role.
2. Review existing entitlements.
3. Identify the requested permission.
4. Review applicable SoD policies and the access-control matrix.
5. Validate the business justification.
6. Determine whether an authorized exception process exists.
7. Identify a compliant alternative.

## Findings

- Robert already has payment-creation permissions.
- The requested approval entitlement may conflict with those permissions.
- The business request is legitimate but does not automatically override security requirements.
- An independent approver is the preferred alternative.

## Root Cause

The request arose from a temporary staffing gap while the regular manager was unavailable.

The security issue is a proposed SoD conflict, not a confirmed unauthorized permission assignment.

## Security Risks

- Fraudulent payment creation and approval
- Unauthorized vendor transactions
- Reduced oversight
- Financial loss
- Audit and compliance findings

## Recommended Resolution

Do not grant the conflicting entitlement through the normal access-request process.

Instead:

1. Identify another employee eligible to approve vendor payments.
2. Obtain the required authorization.
3. Assign only the necessary approval entitlement.
4. Apply a defined expiration date if temporary access is needed.
5. Enable appropriate transaction and access logging.
6. Validate that independent payment approval remains enforced.
7. Document the decision and supporting approvals.

If no alternative exists, refer the request to the organization's formally approved SoD exception process rather than bypassing policy.

## Validation Plan

Verify that:

- Robert cannot approve payments he creates.
- The alternate approver has only the required permissions.
- Temporary access expires as scheduled.
- Payment activity is appropriately logged.
- The SoD policy remains effective.

**Lab status:** Proposed resolution; no live application changes performed.

## Preventive Improvements

- Configure automated SoD conflict detection.
- Integrate access requests with approval workflows.
- Maintain an approved temporary-approver process.
- Conduct periodic entitlement reviews.
- Monitor high-risk financial transactions.

## Lessons Learned

A manager's approval does not automatically authorize an exception to security policy.

IAM Engineers must recognize toxic access combinations and recommend alternatives that support business continuity without weakening security controls.

## Interview Talking Point

This scenario demonstrates how to identify a potential SoD violation, evaluate conflicting entitlements, recommend a compliant alternative, and document an access-governance decision.