# Homelab Infrastructure & Operations Report

**Proxmox VE · Docker Compose · Jellyfin · Homarr · Tailscale · Wazuh**

An engineering report on the modernization and maintenance of a self-hosted media homelab, covering service architecture, migration, private access, dashboard improvements, storage recovery, and backup operations.

**Reporting date** — November 11, 2026, Eastern time  
**Latest availability checks** — November 11, 2026, at 11:15 p.m. Eastern time

| Verified result | Outcome |
| --- | --- |
| Docker services running | **13** |
| Service endpoints responding | **9 of 9** |
| LXC system space recovered through legacy cleanup | **1.22 GiB** |
| Media filesystem space recovered across two removal batches | **19.32 GiB** |
| Media filesystem free after the latest removal | **132.18 GiB** |
| Latest successful local guest backup job | **November 9, 2026** |

[Read the complete report](REPORT.md) · [Download the designed PDF](report.pdf) · [View the printable HTML](report.html) · [Homelab documentation](https://github.com/J0N3B0I/Proxmox-homelab)

<a href="report.pdf"><img src="assets/report-cover.png" alt="Cover of the six-page homelab engineering report" width="360"></a>

## Report coverage

- Proxmox guest architecture and the 13-service Docker stack
- Migration from native applications to Docker Compose
- Tailscale repair and private mobile access
- Homarr dashboard integrations and responsive layout
- Legacy application cleanup and verified filesystem recovery
- User-requested media removal and library reconciliation
- Local backup capacity incident, current status, and follow-up work
- Validation methods and evidence limits

## Publication notes

Operational identifiers, private addresses, account details, credentials, and raw configuration files are omitted from this publication. Media removals are described by aggregate count and recovered space.

Storage figures describe availability inside the named filesystem. Proxmox snapshots can retain blocks after files are removed, so physical pool recovery requires its own measurement.
