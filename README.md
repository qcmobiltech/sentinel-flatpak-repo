# Sentinel Linux Official Flatpak Repository

> **Official Public Application Repository for Sentinel Linux**  
> Hosted at: `https://qcmobiltech.github.io/sentinel-flatpak-repo/`

---

## 🔒 Strict Scope & Repository Policy

1. **Public & General Applications Only:**  
   This repository is open to the public and contains only general consumer, productivity, and standard workstation applications verified for Sentinel Linux.
2. **Open Security Arsenal & Productivity Applications:**  
   The complete **Sentinel Security Toolkit** (99 tools across 16 operational domains including Nmap, Wireshark, Ghidra, ZAP, Cutter, Autopsy, Hashcat, Aircrack-ng, and the native **Sentinel Command Center**) is fully available through this public repository for **all cybersecurity professionals, penetration testers, SecOps engineers, and researchers**. Internal corporate staging shims remain segregated.
---

## 📦 Using This Repository

### Add Remote to Sentinel Linux:
```bash
flatpak remote-add --if-not-exists sentinel https://qcmobiltech.github.io/sentinel-flatpak-repo/sentinel.flatpakrepo
```

### Install Applications:
```bash
flatpak install sentinel org.sentinel.Files
flatpak install sentinel org.sentinel.Terminal
flatpak install sentinel org.sentinel.CommandCenter
flatpak install sentinel org.wireshark.Wireshark
flatpak install sentinel org.ghidra_sre.Ghidra
flatpak install sentinel org.zaproxy.ZAP
flatpak install sentinel re.rizin.cutter
flatpak install sentinel org.sleuthkit.Autopsy
flatpak install sentinel org.sentinel.Vault
flatpak install sentinel org.sentinel.Office
flatpak install sentinel org.sentinel.Calculator
flatpak install sentinel org.sentinel.Media
flatpak install sentinel org.sentinel.Browser
flatpak install sentinel org.sentinel.Boombox
flatpak install sentinel org.sentinel.DesktopEffects
flatpak install sentinel org.sentinel.HardwareFramework
flatpak install sentinel org.sentinel.IPPPrinting
flatpak install sentinel org.sentinel.SupvanPrinting
flatpak install sentinel org.sentinel.SANEAirScan
flatpak install sentinel org.sentinel.Gutenprint
flatpak install sentinel org.sentinel.SANE
flatpak install sentinel org.sentinel.SystemHealth
flatpak install sentinel org.sentinel.Contacts
flatpak install sentinel org.sentinel.PartitionManager
flatpak install sentinel org.sentinel.Photos
flatpak install sentinel org.sentinel.DockEnhancements
flatpak install sentinel org.sentinel.DesktopWidgets
```

---

## 🚀 Adding New Applications

1. Add a Flatpak manifest under `apps/<app-id>.yml`.
2. Ensure the `finish-args` specify appropriate sandbox containment flags corresponding to Sentinel Linux security realms:
   - **User Realm:** Filesystem access mediated via portal.
   - **Office Realm:** Network disabled, documents via portal.
   - **Crypto Realm:** Talks directly to TPM 2.0 PKCS#11, zero raw networking.
   - **Dev Sandbox:** Unprivileged namespace, dri device access.
3. Push to `main`. The GitHub Actions workflow (`.github/workflows/deploy-flatpaks.yml`) will automatically update the OSTree summary and deploy the repository to GitHub Pages.
