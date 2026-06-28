# Project 5 Application Packaging & Deployment (PSADT + Win32)

**Goal:** Package and deploy real applications the enterprise way, wrapping installers with the **PowerShell App Deployment Toolkit (PSADT)**, producing `.intunewin` packages, and deploying through Intune with correct detection rules and staged deployment rings.

** Application Packaging & Deployment (Win32, MSI, EXE, PowerShell).

## What was built
- Packaging workstation on **SRV01** with the **Win32 Content Prep Tool** and **PSADT**.
- Real applications wrapped with PSADT (`Deploy-Application.ps1`) handling silent install, uninstall, and a pre-install close-running-app step, then converted to `.intunewin`.
- Three installation methods are covered across the apps:
  - **EXE** 7-Zip, Notepad++ (file/version detection)
  - **MSI** VLC (MSI product-code detection)
- **Deployment rings:** apps assigned **Available** (on-demand via Company Portal) and **Required** (auto-push), demonstrating both delivery models.

## Proof
| Evidence | File |
|----------|------|
| PSADT packaging folder structure (per-app) | `proof/5-1-packaging-folder.png` |
| `.intunewin` produced by Content Prep Tool | `proof/5-2-intunewin.png` |
| PSADT script 7-Zip | `proof/5-3-7-zip.png` |
| PSADT script Notepad++ | `proof/5-3-notepad++.png` |
| PSADT script VLC (MSI) | `proof/5-3-VLC.png` |
| Apps assigned in Intune | `proof/5-4-intune-apps-assigned.png` |
| Company Portal (Available ring) | `proof/5-7-company-portal.png` |
| Required apps installed | `proof/5-7-company-required-apps.png` |
| 7-Zip installed on endpoint | `proof/5-8-7-zip-installed.png` |
| Notepad++ installed | `proof/5-8-notepad-installed.png` |
| VLC installed (MSI) | `proof/5-8-vlc-installed-msi.png` |
| VLC install (pending state) | `proof/5-8-vlc-installpending.png` |
| All apps installed successfully | `proof/5-8-all-apps-installedsuccessfully.png` |

## Troubleshooting documented (the real-world packaging lesson)
A VLC deployment initially **failed** because an **MSI detection rule was applied to an EXE-packaged app**, the install method and detection method didn't match. Diagnosed via the Intune Management Extension log, then corrected by **repackaging with the vendor MSI** and using the **real MSI product code** for detection. The install-method-vs-detection-method mismatch is the single most common Win32 packaging failure; documenting the fix shows real operational understanding.

> **Note on PSADT in Intune:** Every PSADT package shows `Name: Deploy-Application.exe` in Intune, regardless of the payload, which is the PSADT *launcher*, not the installer. The actual install logic lives inside `Deploy-Application.ps1`.

## Skills
PSADT · Win32 Content Prep Tool · `.intunewin` packaging · detection rules (file/version / MSI product code) · requirement rules · deployment rings (Available vs Required) · MSI / EXE / PowerShell install methods · IME log troubleshooting
