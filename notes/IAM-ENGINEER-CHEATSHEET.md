# IAM Engineer â€” Master Cheat Sheet

**Academy:** IAM Engineer Academy
**Training Organization:** ACME Financial(Simulated)
**Purpose:** Quick reference for IAM concepts, troubleshooting, and interviews.

---

## 1. IAM Fundamentals

| Concept | Meaning |
|---|---|
| Identity | A person, service, device, or workload represented digitally |
| Authentication (AuthN) | Verifying an identity |
| Authorization (AuthZ) | Determining permitted actions |
| MFA | Authentication using two or more distinct factor categories |
| Least Privilege | Granting only the access necessary |
| Need-to-Know | Access based on a legitimate business requirement |
| Entitlement | A specific permission or access right |
| Privileged Access | Access capable of performing sensitive administrative actions |

**Remember:**

Authentication = Who are you?

Authorization = What can you do?

## 2. Identity Lifecycle Management

### Joiner
- Verify HR identity record.
- Provision required accounts.
- Assign birthright access.
- Obtain approval for additional access.
- Validate provisioning.

### Mover
- Verify new role and department.
- Review existing permissions.
- Remove obsolete entitlements.
- Provision newly approved access.
- Validate effective permissions.

### Leaver
- Confirm termination event and effective time.
- Disable appropriate user accounts.
- Revoke sessions and credentials.
- Remove application and privileged access.
- Review workload/service account dependencies.
- Preserve required audit evidence.

**Security risks:** Orphaned accounts, stale access, and privilege accumulation.

## 3. Access Control Models

| Model | Description |
|---|---|
| RBAC | Role-Based Access Control |
| ABAC | Attribute-Based Access Control |
| ACL | Access Control List |
| SoD | Separation of Duties |

**RBAC example:**

DevOps Engineer â†’ Approved DevOps Role â†’ Required Permissions

**ABAC example:**

Allow access when the user's project attribute matches the resource's project attribute and other policy conditions are satisfied.

## 4. Separation of Duties

SoD separates incompatible responsibilities.

**Example toxic combination:**

Create Payment + Approve Payment

Before granting sensitive access:
1. Review existing entitlements.
2. Check SoD policy.
3. Verify business justification.
4. Obtain required approvals.
5. Use a compliant alternative or formal exception process.

## 5. IAM Troubleshooting Workflow

1. **Identity** â€” Who is affected?
2. **Authentication** â€” Can the identity authenticate?
3. **Authorization** â€” What action is denied?
4. **Entitlements** â€” Which groups, roles, and permissions apply?
5. **Policy** â€” Are there explicit restrictions or SoD conflicts?
6. **Approval** â€” Is the requested access authorized?
7. **Remediation** â€” Apply the minimum approved change.
8. **Validation** â€” Confirm expected access and no unintended permissions.
9. **Documentation** â€” Record findings, actions, and evidence.

## 6. Production Ticket Reference

| Ticket | Scenario | Main Concept |
|---|---|---|
| IAM-0001 | Payroll access denied | AuthN vs. AuthZ |
| IAM-0002 | Mover retains production privileges | JML / Least Privilege |
| IAM-0003 | Payment approval conflict | SoD / Access Governance |

## 7. Security Best Practices

- Apply least privilege.
- Prefer standardized roles and groups where appropriate.
- Use MFA for sensitive access.
- Limit and monitor privileged accounts.
- Review access after role changes.
- Revoke access promptly during offboarding.
- Avoid embedding secrets in scripts or repositories.
- Maintain audit logs and change records.
- Validate effective permissions after changes.
- Follow approved access and exception workflows.

## 8. Interview Quick Answers

**Authentication vs. Authorization:** Authentication verifies identity; authorization determines permitted access.

**What is least privilege?** Giving an identity only the permissions required for approved responsibilities.

**What is a Mover event?** A role or department change that triggers an access review and appropriate entitlement changes.

**What is SoD?** Separating incompatible duties to reduce fraud, error, and misuse.

**What is privilege accumulation?** Retaining unnecessary access as responsibilities change.

**What should you do before granting access?** Verify identity, business need, applicable policies, required approval, and least privilege.

---

## Future Topics to Add

- Active Directory and Group Policy
- Microsoft Entra ID
- AWS IAM policies and roles
- SAML, OAuth 2.0, and OpenID Connect
- Okta and SSO
- SailPoint and access certifications
- CyberArk and Privileged Access Management
- PowerShell and Python IAM automation
- IAM governance and audit evidence

**Last updated:** Day 3 â€” IAM Foundations
