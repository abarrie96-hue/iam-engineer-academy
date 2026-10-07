# IAM-0001 — Payroll Application Access Denied

## Ticket Information

| Field | Value |
|---|---|
| Ticket ID | IAM-0001 |
| Organization | ACME Financial (Simulated) |
| Category | Access Management |
| Affected User | Sarah Johnson |
| Department | Finance |
| Status | Training Scenario — Proposed Resolution |

## Incident Description

Sarah Johnson reports that she cannot access the Payroll application.

She can successfully authenticate to the employee portal using her credentials and MFA, but the Payroll application displays:

**Access Denied**

## Initial Investigation

1. Verify Sarah's identity and the affected application.
2. Confirm whether authentication was successful.
3. Identify the specific resource and authorization failure.
4. Review group memberships, roles, and application assignments.
5. Compare current access against the approved access requirements.

## Findings

- Authentication was successful.
- The Payroll application denied authorization.
- Sarah was missing membership in `Payroll-Users`.

## Root Cause

The user did not have the required Payroll application entitlement.

The underlying reason for the missing assignment has not yet been established.

## Security Considerations

Before granting access, confirm:

- Sarah has a legitimate business need.
- The appropriate application owner or authorized approver approves the request.
- The requested access complies with least privilege.
- No conflicting access or policy restrictions apply.

## Proposed Remediation

1. Confirm the required authorization and approvals.
2. Add Sarah to `Payroll-Users` if approved.
3. Allow directory/application synchronization where applicable.
4. Have Sarah retry access.
5. Verify the resulting permissions are appropriate.

## Validation

The following checks should be completed in a real environment:

- Authentication succeeds.
- Payroll access works as approved.
- No unnecessary privileged access was granted.
- Group membership is documented.

**Lab status:** Proposed resolution; no live application change performed.

## Lessons Learned

Successful authentication does not guarantee authorization.

An IAM Engineer must investigate entitlements and verify business approval before changing access.

## Interview Talking Point

This scenario demonstrates how to distinguish an authentication problem from an authorization problem and apply least privilege during access remediation.