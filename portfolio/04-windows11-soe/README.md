# Project 4 Windows 11 SOE + Security Baselines  🔜 *In progress*

**Goal:** Harden the enrolled Windows 11 endpoint into a documented **Standard Operating Environment (SOE)** with Microsoft security baselines, BitLocker with Entra key escrow, and Defender.

** Windows 11 SOE; security baselines; device hardening.

## Planned build
1. **Windows Security Baseline** (Intune → Endpoint security → Security baselines) applied and **tuned**, not blind-accepted (BitLocker items deferred to a dedicated policy to avoid conflict).
2. **Configuration profiles** (Settings catalog): SmartScreen, removable-storage controls, Credential Guard.
3. **BitLocker** (Endpoint security → Disk encryption) with **recovery key escrow to Microsoft Entra ID** and client-driven rotation.
4. **Microsoft Defender Antivirus** policy (real-time, cloud-delivered protection, PUA blocking).
5. **SOE Build Standard** document versioned, every setting + rationale, with known VM limitations noted.

## Proof (to capture)
- Security baseline profile + a tuned setting + device "Succeeded" report
- BitLocker policy showing "Save recovery info to Entra ID = Required"
- **Recovery key visible in Entra → Devices → BitLocker keys** *(headline proof)*
- `manage-bde -status C:` → Protection On / 100%
- `Get-MpComputerStatus` → RealTimeProtectionEnabled: True

## Skills
Security baselines · BitLocker + Entra key escrow · Microsoft Defender · device hardening · SOE documentation
