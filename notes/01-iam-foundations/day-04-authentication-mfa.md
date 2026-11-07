# Day 4 — Authentication, MFA and Passwordless Security

## Learning Objectives

- Understand authentication factors and MFA methods.
- Explain passwordless authentication and FIDO2.
- Recognize MFA fatigue attacks.
- Investigate suspicious authentication activity.
- Troubleshoot Microsoft Authenticator failures.

## Authentication Factors

| Factor | Example |
|---|---|
| Something you know | Password or PIN |
| Something you have | Security key or authenticator device |
| Something you are | Fingerprint or facial recognition |

MFA requires at least two distinct authentication factor categories.

## MFA Methods

- SMS verification codes
- Authenticator application push notifications
- Time-based one-time passwords (TOTP)
- FIDO2 security keys
- Passkeys

SMS and ordinary push approvals are not phishing-resistant. FIDO2 authentication provides phishing resistance through cryptographic verification bound to the legitimate service.

## Passwordless Authentication

Passwordless authentication eliminates the need to enter a traditional account password.

FIDO2 passkeys use public-key cryptography. The private key remains protected by the authenticator, while the service uses the registered public key to verify authentication.

## MFA Fatigue

MFA fatigue occurs when an attacker repeatedly triggers authentication requests, hoping the user eventually approves one.

Unexpected MFA requests should be reported and investigated.

## Authentication Troubleshooting

1. Verify the affected identity.
2. Review authentication and sign-in logs.
3. Examine MFA results and Conditional Access policies.
4. Check registered authentication methods.
5. Verify device connectivity and authenticator functionality.
6. Follow secure recovery procedures when necessary.
7. Test authentication and document the outcome.

## Production Ticket — IAM-0004

**Scenario:** Jennifer Adams receives seven unexpected MFA requests and reports that she did not initiate them.

A subsequent successful sign-in from an unfamiliar device raises concerns about possible account compromise.

### Investigation

- Review source IP addresses.
- Examine device and browser information.
- Check MFA results.
- Review Conditional Access policies.
- Investigate successful sessions and account changes.

### Containment and Remediation

- Escalate through the incident-response process.
- Revoke sessions and temporarily block sign-in when appropriate.
- Reset compromised credentials.
- Review registered MFA methods.
- Investigate unauthorized account changes.
- Validate security before restoring access.

### Follow-Up Issue

Jennifer reports that Microsoft Authenticator is not sending notifications after account recovery.

**Troubleshooting:**

1. Review authentication logs and selected MFA method.
2. Check authenticator registration, device connectivity, and notification settings.
3. Use approved MFA recovery and re-registration procedures if needed.
4. Test sign-in and document the outcome.

**Status:** Simulated training scenario; no live account changes performed.

## Interview Notes

**Q: What is MFA fatigue?**

An attack in which repeated MFA prompts are sent to a user in an attempt to obtain an accidental or frustrated approval.

**Q: How would you troubleshoot missing MFA notifications?**

Review sign-in logs and authentication methods, verify device registration and notification delivery, and use secure recovery procedures if re-registration is required.

## Key Takeaways

- MFA strengthens authentication.
- Not every MFA method is phishing-resistant.
- FIDO2 and passkeys provide stronger phishing protection.
- Unexpected MFA requests may indicate attempted account compromise.
- Containment, investigation, remediation, and validation are essential.
- MFA resets require proper identity verification.