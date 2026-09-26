# Sentinel Linux Official Flatpak Repository

> **Official Public Application Repository for Sentinel Linux**  
> Hosted at: `https://qcmobiltech.github.io/sentinel-flatpak-repo/`

---

## 🔒 Strict Scope & Repository Policy

1. **Public & General Applications Only:**  
   This repository is open to the public and contains only general consumer, productivity, and standard workstation applications verified for Sentinel Linux.
2. **Company-Exclusive Apps STRICTLY FORBIDDEN:**  
   Internal, proprietary, and engineer-exclusive tooling (such as **ClientCore**, hardware diagnostic tools, internal telemetry agents, and staging utilities) are **STRICTLY PROHIBITED** from this repository. They are maintained and distributed exclusively through the private **`sentinel-engineer-flatpaks`** repository.

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
flatpak install sentinel org.sentinel.Vault
flatpak install sentinel org.sentinel.Office
flatpak install sentinel org.sentinel.Calculator
flatpak install sentinel org.sentinel.Media
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
