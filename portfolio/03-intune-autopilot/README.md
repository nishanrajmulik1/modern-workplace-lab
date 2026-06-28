# Project 3 — Intune Enrollment + Windows Autopilot

**Goal:** Provision a Windows 11 endpoint zero-touch via **Windows Autopilot (user-driven)** into Microsoft Intune, landing it Entra-joined, managed, and compliant.

**Maps to JD:** Microsoft Intune & Endpoint Management; Windows Autopilot deployment.

## What was built
- Automatic MDM enrollment enabled (Entra → Mobility → Intune, MDM scope = All).
- Device **hardware hash** captured with `Get-WindowsAutopilotInfo` and imported into Intune.
- **User-driven Autopilot deployment profile** (Microsoft Entra joined) + **Enrollment Status Page**, assigned to a dynamic device group.
- Device provisioned end-to-end through OOBE → ESP → desktop, **Entra-joined and Intune-managed**.

## Proof
| Evidence | File |
|----------|------|
| Autopilot device — Profile status = Assigned | `proof/3-1-MLG-Client01-Profile-Assigned.png` |
| Autopilot deployment profile (user-driven) | `proof/3-2-AP-MLG-User-Driven.png` |
| Enrollment Status Page during OOBE | `proof/3-2-AP-OOBE.png` |
| OOBE provisioning completed | `proof/3-2-AP-OOBE-Completed.png` |
| Device Entra-joined (`dsregcmd /status`) | *(see `01-azureadjoined.png`)* |

## Troubleshooting documented
- **SMBIOS serial collision** — the VM registered with a placeholder serial (`SMBIOS_STRING_INDEX_0`). Set a real SMBIOS serial in Proxmox, re-captured the hash, and re-imported.
- **DNS suffix poisoning** — pfSense DHCP supplied a bad domain suffix that mangled `login.microsoftonline.com` resolution and prevented Autopilot from matching its profile; corrected the DHCP domain-name field.
- **CA enrollment block** — the require-compliant-device policy blocked the unmanaged device mid-enrollment; resolved with an Intune-enrollment exclusion (see Project 2).

## Note on join type
The device is **Microsoft Entra joined** (cloud-only) per the user-driven profile, so `DomainJoined: NO` is expected and correct. `TpmProtected: YES` confirms the device identity key is bound to the (virtual) TPM.

## Skills
Windows Autopilot · Intune MDM enrollment · Enrollment Status Page · dynamic device targeting · device compliance · OOBE troubleshooting

**Résumé line:** *Configured user-driven Windows Autopilot with an Enrollment Status Page and ran full zero-touch provisioning into Intune — device enrolled corporate-owned, Entra-joined, and compliant.*
