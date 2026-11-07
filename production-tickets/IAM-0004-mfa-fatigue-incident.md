# IAM-0004 — MFA Fatigue Attack and Account Compromise

## Ticket Information

| Field | Value |
|---|---|
| Ticket ID | IAM-0004 |
| Organization | ACME Financial (Simulated) |
| Category | Identity Security / Authentication |
| Priority | High |
| Affected User | Jennifer Adams |
| Department | Finance |
| Status | Training Scenario — Proposed Resolution |

## Incident Description

Jennifer Adams reports receiving seven unexpected Microsoft Authenticator approval notifications within ten minutes.

Jennifer states that she did not initiate any of the authentication attempts and denied the requests.

During the investigation, an unfamiliar successful sign-in is discovered.

The security team subsequently confirms that Jennifer's password was compromised.

## Initial Investigation

1. Verify Jennifer's identity through an approved process.
2. Review Microsoft Entra ID sign-in logs.
3. Identify suspicious source IP addresses.
4. Examine device information and authentication details.
5. Review MFA approval and denial events.
6. Inspect Conditional Access policy results.
7. Investigate successful sign-ins and potentially unauthorized sessions.
8. Escalate the incident to the security response team.

## Findings

- Multiple unexpected MFA requests were reported.
- Jennifer denied the suspicious requests.
- An unfamiliar successful sign-in was identified.
- Jennifer's password was confirmed compromised.
- Potential unauthorized access requires further investigation.

## Root Cause

The confirmed credential compromise enabled an attacker to attempt authentication.

The repeated MFA prompts are consistent with an MFA fatigue attack intended to persuade the user to approve an unauthorized sign-in.

The mechanism behind the unfamiliar successful sign-in has not been established.

## Security Risks

- Unauthorized account access
- Exposure of sensitive financial information
- Session hijacking
- Unauthorized application access
- Privilege misuse
- Potential lateral movement

## Containment

Follow approved incident-response procedures:

1. Notify the security incident-response team.
2. Preserve relevant authentication evidence.
3. Temporarily block the affected account when appropriate.
4. Revoke active sessions and address application sessions or tokens that may remain valid.
5. Investigate suspicious sign-ins and account activity.
6. Prevent further unauthorized authentication attempts.

## Proposed Remediation

1. Reset Jennifer's compromised password through a secure process.
2. Review registered MFA methods and devices.
3. Remove unauthorized authentication methods.
4. Review suspicious account changes and role assignments.
5. Verify Conditional Access and MFA enforcement.
6. Investigate possible unauthorized activity following the successful sign-in.
7. Obtain the appropriate clearance before restoring account access.

## Validation

Before restoring normal access:

- Confirm compromised credentials have been replaced.
- Confirm unauthorized authentication methods have been removed.
- Address suspicious sessions and access tokens.
- Verify applicable MFA and Conditional Access policies.
- Confirm no unresolved unauthorized account changes remain.
- Test an authorized sign-in.
- Record evidence and the final incident disposition.

## Follow-Up — Missing MFA Notifications

After account recovery, Jennifer reports that Microsoft Authenticator no longer sends approval notifications.

### Troubleshooting Procedure

1. Review sign-in logs and authentication requirements.
2. Confirm the authentication method selected for the sign-in.
3. Verify the correct account and authenticator registration.
4. Check device connectivity and notification permissions.
5. Review applicable Conditional Access policies.
6. If necessary, use an approved MFA recovery and re-registration procedure.
7. Test authentication and document the outcome.

## Preventive Improvements

- Prefer phishing-resistant MFA such as FIDO2 security keys or passkeys.
- Use number matching where supported for push authentication.
- Monitor repeated MFA denials and unusual sign-in patterns.
- Apply risk-based authentication and Conditional Access controls.
- Train employees to report unexpected MFA requests.
- Protect authentication-method recovery processes against social engineering.

## Lessons Learned

MFA reduces account-compromise risk, but some methods remain vulnerable to phishing and social engineering.

IAM Engineers must prioritize containment when unauthorized access is suspected and validate account security before restoring access.

## Interview Talking Point

This scenario demonstrates the investigation of an MFA fatigue attack, analysis of Microsoft Entra ID sign-in activity, account containment, credential recovery, and secure restoration of access.

## Portfolio Evidence

**Scenario type:** Simulated production incident

**Live environment changes:** None

**Evidence:** Written investigation, proposed remediation, and validation procedures.