# IAM-0007 — Privileged Access Review

**Organization:** ACME Corporation
**Environment:** Active Directory — acme.test
**Request Type:** Privileged Access Review
**Account:** adm.michael.johnson
**Status:** Pending Final Verification

## 1. Business Requirement

Michael Johnson requires password-reset permissions for standard employee accounts without receiving Domain Administrator privileges.

## 2. Access Configuration

- Administrative account: adm.michael.johnson
- Delegated security group: SG-Helpdesk-PasswordReset
- Target OU: OU=Users,OU=ACME,DC=acme,DC=test
- Delegated permission: Reset Password

## 3. Verification Checklist

- [x] Dedicated administrative account created
- [x] Administrative account added to helpdesk security group
- [x] Password-reset delegation configured
- [x] Password reset tested successfully using administrative credentials
- [x] Domain Admin membership check returned no results
- [x] Final privileged group membership review completed
- [x] Delegated permissions verified in the OU ACL

## 4. Security Principles

- Principle of Least Privilege
- Role-Based Access Control
- Privileged Access Management
- Separation of Administrative and Standard Accounts

## 5. Findings

The delegated password-reset test succeeded without Domain Admin membership.

A final review of other privileged memberships and delegated permissions is required before concluding that the account has only the intended access.

## 6. Resolution

Pending final verification and documentation.
