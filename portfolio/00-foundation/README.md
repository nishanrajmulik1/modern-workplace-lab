# Project 0 - Foundation: Tenant, Licensing & Groups

**Goal:** Establish the Microsoft 365 tenant, licensing, identities, and the Entra groups for every later project target.

## What was built
- Microsoft 365 **E3** tenant under the fictional company **MyLogiGroup** (`MyLogiGroup.onmicrosoft.com`).
- Verified custom public domain, so user sign-in uses a routable UPN.
- Test identities licensed for Intune and Entra ID P1.
- **Dynamic device groups** for Autopilot/Intune targeting.

## Why E3
Microsoft 365 E3 includes **Microsoft Entra ID P1** (Conditional Access, MFA), **Microsoft Intune**, **Windows 11 Enterprise**, and **Defender for Endpoint P1** - sufficient for hybrid identity, Conditional Access, Autopilot, SOE hardening, and app packaging. (Risk-based Conditional Access and EDR risk-score compliance require P2/E5 and are documented as out of scope.)

## Proof
| Evidence | File |
|----------|------|
| Custom domain verified in tenant | `proof/00-domain-verified.png` |
| Microsoft 365 E3 licensing | `proof/00-e3-licensing.png` |

## Skills
M365 administration · Entra ID P1 · domain verification · dynamic device groups · licensing design

