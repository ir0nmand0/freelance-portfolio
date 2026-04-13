# Enterprise Recovery Platform

**Client:** NDA client (Fortune 500 energy company subsidiary)
**Role:** Sole developer
**Duration:** 1.5 years
**Status:** Production (deployed to 1,000+ sites)

---

## Problem

When hardware fails at one of the company's 1,000+ remote sites (gas stations), field engineers faced:

1. **4+ hour recovery time** — manual procedures with no standardized tooling
2. **Configuration diversity** — each site type had unique OS, drivers, and application configs, making a one-size-fits-all approach impossible
3. **Distribution at scale** — getting updated recovery media to 1,000+ geographically dispersed sites was itself a logistics problem
4. **Offline environments** — many sites have limited or no internet connectivity

## Solution

Built an automated multi-boot recovery system with a complete distribution pipeline:

**Image Build System:**
- Docker-based build pipeline (reproducible, runs in CI)
- 3 image types: full ISO (with diagnostics), lite ISO, bootable IMG
- Multi-boot support for different OS versions (Astra Linux domain/non-domain, Windows)
- Companion `initramfs-modifier` — patches Debian initramfs for USB multi-boot via bind mount
- Kaspersky antivirus integration with automated database updates
- SHA256 integrity verification at every stage

**Distribution Pipeline:**
- `iso_rescue_diff_checker` → detects what changed since last build
- `rescue-forge` → builds updated ISO/IMG
- `chameleon-file-proxy` → uploads to SFTPGo FTP server
- `torrent-forge` → creates private .torrent files
- `opentracker-docker` → private BitTorrent tracker with IP whitelist
- Field engineers download via BitTorrent (efficient for large files over limited WAN)

**OS Migration (companion project):**
- 3-stage remote migration pipeline: PowerShell/SCCM → SystemRescue → Astra Linux
- GRUB 2.06/GRUB4DOS/BCD patching for bootloader transition
- Disk operations: smartctl diagnostics, ntfsresize, GPT/MBR conversion
- Rollback capability at every stage
- 11 specialized Windows images for different site types and security requirements

## Result

| Metric | Value |
|--------|-------|
| MTTR | **4 hours → 45 minutes** (89% reduction) |
| Deployment | **1,000+ sites** across national network |
| OS migration | **95% of workstations** migrated (Windows → Astra Linux) |
| Adoption | Used by all field engineering teams |
| Windows images | **11 specialized builds** for different security/compliance profiles |
| Build reproducibility | 100% — Docker-based, SHA256-verified |

## Tech Stack

`Bash` `Docker` `SystemRescue` `PowerShell` `SCCM` `Python` `GRUB2` `BitTorrent` `OpenTracker` `SFTPGo` `Kaspersky` `Ansible`
