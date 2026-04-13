# Enterprise OS Migration & Recovery Platform

**Client:** NDA client (Fortune 500 energy company subsidiary)
**Role:** Developer. Trained field engineering teams on the platform after deployment
**Duration:** 2+ years
**Status:** Production (deployed to 1,000+ sites)

---

## Problem

Fortune 500 energy company needed to migrate thousands of workstations from Windows to Linux across 1,000+ remote sites (gas stations). Critical constraints:

1. **No physical access** — sites are geographically dispersed across the country, sending engineers to each one was not feasible
2. **Zero downtime tolerance** — gas stations operate 24/7, migration must not disrupt sales
3. **Configuration diversity** — 11 different hardware/software/security profiles across site types
4. **Rollback requirement** — if migration fails at any stage, the machine must boot back into Windows automatically
5. **Post-migration recovery** — when hardware fails after migration, field engineers needed 4+ hours for manual recovery

## Solution

Built a 3-stage **fully remote** OS migration pipeline + automated recovery platform:

**Remote Migration Pipeline (the core innovation):**
- **Stage 1 — PowerShell/SCCM**: Pushed remotely to all Windows machines via corporate SCCM. Prepares dual-boot: patches BCD (Boot Configuration Data), installs GRUB 2.06/GRUB4DOS bootloader alongside Windows, SHA256-verifies all payloads. Machine reboots into Stage 2 automatically
- **Stage 2 — SystemRescue (Linux live environment)**: Runs disk diagnostics (smartctl), resizes NTFS partition (ntfsresize) to make room, converts partition table if needed (GPT/MBR). Installs Linux to freed space. If any step fails → automatic rollback to Windows boot
- **Stage 3 — Linux post-install**: Site-specific configuration applied based on hardware profile. Domain/non-domain variants via custom initramfs patches (bind mount technique)
- **11 specialized images** for different site types and security/compliance requirements (domain, non-domain, BitLocker, KSC integration, etc.)

**Recovery Platform (for post-migration failures):**
- Docker-based multi-boot rescue image builder (3 types: full ISO, lite ISO, bootable IMG)
- Integrated antivirus with automated database updates
- SHA256 integrity verification at every stage

**Distribution Pipeline (serves both migration and recovery):**
- Automated build: `diff_checker` → `rescue-forge` → `file-proxy` (SFTPGo) → `torrent-forge` → private BitTorrent tracker
- Field engineers download large images via BitTorrent over limited WAN — efficient and resumable

## Result

| Metric | Value |
|--------|-------|
| OS migration | **95% of workstations** migrated Windows → Linux remotely, zero physical site visits |
| Migration images | **11 specialized builds** covering all site types and security profiles |
| Rollback rate | **<2%** — automatic rollback to Windows on failure |
| Recovery MTTR | **4 hours → 45 minutes** (89% reduction) for post-migration hardware failures |
| Scale | **1,000+ sites** across national network |
| Adoption | Used by all field engineering teams, documentation and training delivered |
| Build reproducibility | 100% — Docker-based, SHA256-verified |

## Tech Stack

`Bash` `PowerShell` `SCCM` `Python` `Docker` `SystemRescue` `GRUB2` `GRUB4DOS` `BCD` `ntfsresize` `smartctl` `initramfs` `BitTorrent` `OpenTracker` `SFTPGo` `Ansible`
