# Day 2 — Identity Lifecycle Management (JML)

## Learning Objectives

- Understand Identity Lifecycle Management (ILM).
- Explain Joiner, Mover, and Leaver processes.
- Differentiate provisioning from deprovisioning.
- Identify privilege accumulation and orphaned accounts.
- Understand how IAM Engineers handle service accounts.

## Key Concepts

### Identity Lifecycle Management

Identity Lifecycle Management controls an identity's access throughout its relationship with an organization.

The three major lifecycle events are **Joiner, Mover, and Leaver (JML)**.

### Joiner

A new employee joins the organization.

Typical workflow:

1. HR creates the employee record.
2. The IAM platform receives the identity information.
3. Accounts are provisioned.
4. Birthright access is assigned.
5. Role-specific access is granted after required approvals.
6. Access is validated and documented.

### Mover

An employee changes departments, roles, or responsibilities.

Typical workflow:

1. HR updates the employee record.
2. IAM identifies the role change.
3. Existing entitlements are reviewed.
4. Unnecessary access is removed.
5. New authorized access is provisioned.
6. Changes are validated and documented.

**Major risk:** Privilege accumulation, where employees retain access from previous roles.

### Leaver

An employee leaves the organization.

Typical workflow:

1. Confirm the authoritative termination event.
2. Disable interactive accounts at the effective termination time.
3. Revoke active sessions and credentials.
4. Remove application and privileged access.
5. Review service-account ownership and dependencies.
6. Validate deprovisioning.
7. Document actions for audit evidence.

## Important Terminology

**Provisioning:** Creating accounts and/or granting access.

**Deprovisioning:** Removing access and/or disabling accounts.

**Birthright Access:** Standard access automatically granted based on qualifying employment attributes.

**Entitlement:** A specific access right or privilege.

**Orphaned Account:** An account without appropriate active ownership or lifecycle management.

**Privilege Accumulation:** Retention of permissions that are no longer required.

**Authoritative Source:** The trusted system providing identity information, commonly an HR platform for employee lifecycle events.

## Production Ticket — IAM-0002

### Scenario

Michael Thompson transferred from Engineering to Finance.

His new Finance access was provisioned, but he retained:

- `DevOps-Engineers`
- `AWS-Production-Admin`
- `Jenkins-Production`

### Root Cause

The Mover lifecycle process did not remove obsolete entitlements.

### Security Risk

Michael retained privileged access beyond his current job requirements, creating privilege accumulation.

### Investigation

Before revoking access, verify:

- Whether the access has a valid business justification.
- Whether an approved exception exists.
- Whether temporary access has an expiration date.
- Whether the appropriate owner or manager has authorized continued access.

### Remediation

Once the access is confirmed unnecessary:

1. Identify obsolete entitlements.
2. Remove unauthorized or unnecessary access.
3. Validate that old access is no longer effective.
4. Confirm required Finance access still functions.
5. Document evidence and close the ticket.

## Service Account Considerations

A service account used by a production application should not automatically be disabled when its previous owner leaves.

Instead:

1. Identify the service account's purpose.
2. Determine its dependencies.
3. Assign a new accountable owner.
4. Remove the departing employee's access.
5. Rotate credentials when appropriate.
6. Validate that dependent services continue functioning.

## Interview Notes

**Q: Explain Joiner, Mover, and Leaver.**

Joiner provisions identities and appropriate access for new employees. Mover reevaluates access when responsibilities change, removing unnecessary permissions and assigning new authorized entitlements. Leaver disables identities, revokes sessions, and removes access when the employment relationship ends.

These processes help prevent privilege accumulation, stale access, and orphaned accounts.

## What I Learned

A successful Mover process must review both old and new access.

A Leaver process must distinguish human identities from service identities to avoid disrupting production systems.

## Key Takeaways

- Joiner = Provision appropriate access.
- Mover = Review, remove, and reassign access.
- Leaver = Revoke and deprovision access.
- Always validate and document IAM changes.