# Day 3 — Access Control: RBAC, ABAC & Separation of Duties

## Learning Objectives

- Understand Role-Based Access Control (RBAC).
- Understand Attribute-Based Access Control (ABAC).
- Differentiate groups, roles, permissions, and entitlements.
- Explain Separation of Duties (SoD).
- Identify toxic combinations of access.
- Understand how to design an enterprise access matrix.

## Key Concepts

### Permission

A permission allows an identity to perform a specific action on a resource.

**AWS examples:**
- `ec2:DescribeInstances`
- `s3:GetObject`
- `ec2:StartInstances`
- `ec2:TerminateInstances`

### Group

A collection of identities used to simplify access management.

Example:

`DevOps-Engineers` contains David, Jane, and Michael.

Instead of managing every employee individually, IAM administrators can manage access through group memberships.

### Role

A role represents a defined function or set of responsibilities.

Examples:
- DevOps Engineer
- Security Analyst
- IAM Engineer
- Payroll Administrator
- Database Administrator

Roles can be mapped to the access required for those responsibilities.

### RBAC — Role-Based Access Control

RBAC assigns permissions based on predefined roles.

Example:

User → DevOps Engineer Role → Approved DevOps Access

**Benefits:**
- Standardized access
- Easier administration
- Improved auditing
- More consistent lifecycle management

### ABAC — Attribute-Based Access Control

ABAC evaluates attributes associated with identities, resources, actions, or the environment.

Example policy:

Allow access when:
- User department = Engineering
- User project = Phoenix
- Resource project = Phoenix
- Resource environment = Development

ABAC supports more granular access decisions.

### RBAC vs. ABAC

**RBAC:** What role does the identity have?

**ABAC:** Do the relevant attributes satisfy the access policy?

Organizations may combine both models.

### Entitlement

A specific access right or privilege granted to an identity.

Examples:
- `Payroll-Users`
- `AWS-Production-ReadOnly`
- `Jenkins-Users`
- `Database-Admins`

### Direct Permission Assignments

Direct assignments grant permissions to individual identities rather than through standardized roles or groups.

They are not always inappropriate, but they can be difficult to review, maintain, and remove during employee transfers.

## Separation of Duties (SoD)

SoD divides sensitive responsibilities so one identity cannot independently perform incompatible stages of a critical business process.

Example:

- Employee A creates a payment.
- Employee B approves the payment.

This reduces the risk of fraud, error, and abuse.

### Toxic Combination

A toxic combination occurs when an identity possesses conflicting entitlements that create unacceptable risk.

Example:

`Create Payment` + `Approve Payment`

A toxic combination may violate an organization's SoD policy.

## Access Matrix

An access matrix documents which roles should have access to specific resources.

| Role | AWS | GitHub | Payroll | IAM Admin |
|---|---|---|---|---|
| Developer | Development | Yes | No | No |
| DevOps Engineer | Limited Dev/Prod | Yes | No | No |
| Security Analyst | Security Read | Limited | No | No |
| IAM Engineer | IAM-related | Limited | No | Authorized IAM access |
| Payroll Administrator | No | No | Yes | No |

This is an illustrative model. Actual permissions must be defined and approved by resource owners.

## Production Ticket — IAM-0003

### Scenario

Robert Miller is an Accounts Payable Specialist.

Current entitlements:
- Create Vendor
- Create Payment

Requested entitlement:
- Approve Vendor Payments

Business justification:
His manager is on vacation, and payments must continue.

### Security Concern

Granting approval permissions would potentially create an SoD conflict because Robert could create and approve payments.

### Investigation

1. Identify the requested entitlement.
2. Review Robert's existing access.
3. Check applicable SoD and security policies.
4. Verify the business justification.
5. Determine whether appropriate independent approval or exception procedures exist.

### Recommended Resolution

Do not automatically grant the conflicting permission.

Instead, identify another appropriately authorized employee who can temporarily approve payments.

The temporary access should have:
- Appropriate approval
- Defined business justification
- Limited permissions
- Expiration date
- Audit logging

### Important Principle

**Business approval does not automatically override security policy.**

## Interview Notes

**Q: What is the difference between RBAC and ABAC?**

RBAC grants access based primarily on predefined roles. ABAC evaluates attributes associated with identities, resources, actions, or environmental context.

**Q: What is Separation of Duties?**

SoD is a security control that separates incompatible responsibilities to reduce fraud, error, and unauthorized activity.

**Q: What would you do if a manager approved an SoD-conflicting access request?**

Review the applicable security policy and approved exception process. Seek a compliant alternative rather than granting conflicting access solely because a manager approved it.

## What I Learned

An IAM Engineer must evaluate business requirements alongside security policies.

Manager approval alone does not guarantee that requested access is appropriate.

Access should be granted through standardized roles and groups where practical, with appropriate governance and auditing.

## Key Takeaways

- RBAC = Access based on roles.
- ABAC = Access based on attributes.
- Groups simplify access management.
- Entitlements represent specific access rights.
- SoD separates incompatible responsibilities.
- Toxic combinations create security risks.
- Access requests must follow organizational security policies.