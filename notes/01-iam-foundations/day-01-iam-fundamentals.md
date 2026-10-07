# Day 1 — IAM Fundamentals

## Learning Objectives

- Understand Identity and Access Management (IAM).
- Differentiate authentication from authorization.
- Explain the Principle of Least Privilege.
- Identify common IAM troubleshooting scenarios.

## Key Concepts

### Identity
A digital representation of a person, application, service, device, or workload.

### Authentication (AuthN)
Verifies an identity.

**Question:** Who are you, and can you prove it?

Examples: Passwords, MFA, security keys.

### Authorization (AuthZ)
Determines what an authenticated identity is permitted to access or perform.

**Question:** What are you allowed to do?

### Principle of Least Privilege
Grant only the minimum permissions necessary to perform authorized responsibilities.

### Need-to-Know
Access should be supported by a legitimate business requirement.

### Time-Bound Access
Temporary access with a defined expiration time.

## Troubleshooting Workflow

1. Identify the affected identity.
2. Determine whether authentication succeeded.
3. Identify the resource and requested action.
4. Review relevant groups, roles, and entitlements.
5. Check applicable authorization policies.
6. Verify the business justification and approval.
7. Implement an authorized correction.
8. Validate access and document the result.

## Production Ticket

**IAM-0001 — Payroll Access Denied**

A Finance employee can successfully authenticate but receives an Access Denied message when opening the Payroll application.

**Investigation:** Authentication succeeded, so examine application authorization, group membership, and access assignments.

**Finding:** The employee is missing the `Payroll-Users` group.

**Required action:** Verify business need and approval before assigning the missing entitlement. Validate access afterward.

## Interview Notes

**Q: What is the difference between authentication and authorization?**

Authentication verifies identity. Authorization determines which resources and actions that identity is permitted to access.

## What I Learned

Successful authentication does not guarantee access to every resource. An IAM Engineer must verify authorization requirements before changing permissions.

## Key Takeaway

**Authentication = Prove your identity.**

**Authorization = Determine permitted access.**