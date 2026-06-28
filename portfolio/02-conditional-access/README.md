# Project 2 — Conditional Access Baseline (Zero Trust)

**Goal:** Build a Zero-Trust Conditional Access baseline that enforces MFA, blocks legacy authentication, and requires managed devices — with a safe rollout and an emergency-access account.

**Maps to JD:** Conditional Access integrations; Zero Trust security controls.

## What was built
- A **break-glass (emergency access) Global Admin account**, excluded from every CA policy — the standard anti-lockout safeguard.
- **Security Defaults disabled** (required before custom CA policies take effect).
- Three baseline policies, rolled out **report-only first, then enforced**:
  1. **Require MFA** for all users (break-glass excluded).
  2. **Block legacy authentication.**
  3. **Require compliant or Hybrid-joined device** for Microsoft 365.

## Proof
| Evidence | File |
|----------|------|
| Conditional Access policy list | `proof/2-1-ca-policies.png` |
| MFA policy detail | `proof/2-2-MFA-policy.png` |
| MFA policy with break-glass exclusion | `proof/2-2-MFA-policy-excluded-break-glass.png` |
| Break-glass account (Global Admin) | `proof/2-3-break-glass-account.png` |
| Sign-in logs — CA applied | `proof/2-4-sign-in-logs.png` |
| MFA required at sign-in | `proof/2-4-MFA-required.png` |
| MFA satisfied | `proof/2-4-MFA-satisfied.png` |
| MFA registration | `proof/2-4-MFA-setup.png` |
| Test user login | `proof/2-4-testuser-login.png` |

## Live enforcement proof
During Autopilot enrollment, the device-compliance CA policy **correctly blocked an unmanaged device** ("You can't get there from here" — error 53001), then enrollment succeeded once the device became managed. This is live evidence the Zero-Trust control actually enforces — and the project documents the standard fix: excluding **Microsoft Intune Enrollment** from the require-compliant-device policy so devices can enroll, then become compliant.

## Skills
Conditional Access · Zero Trust · MFA · legacy-auth blocking · break-glass design · report-only rollout · device-based access control

**Résumé line:** *Designed a Conditional Access baseline (MFA, legacy-auth block, device-based access) with a documented break-glass exclusion and report-only-to-enforce rollout.*
