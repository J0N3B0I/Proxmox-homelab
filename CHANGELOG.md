# Homelab change log

## 2026-11-24

### Complete plain-English Wazuh process guide

Published a six-page [downloadable process guide](https://github.com/J0N3B0I/Wazuh-FIM-Lab/blob/main/complete-process-guide.pdf) and an editable reading copy. The guide explains the dedicated VM build, restricted networking, Wazuh enrollment, real-time file-change tests, package updates, kernel exposure restrictions, per-CVE vendor review, and post-reboot validation. It distinguishes completed work from remaining findings, future patching, and the backup capacity gap. It records previously verified outcomes rather than claiming a new live security audit. No service configuration changes were required to produce the guide.

### Remaining kernel findings review and targeted lab protections

Reviewed the remaining FIM practice guest's kernel findings against Ubuntu's per-CVE status for the `linux` source package and Noble release. Published the [review and operating limits](https://github.com/J0N3B0I/Wazuh-FIM-Lab/blob/main/docs/kernel-findings-review.md), a per-CVE spreadsheet, and post-reboot validation evidence. Vendor-status reconciliation does not establish individual exploitability for every record.

Blocked normal loading of the unused Xen network backend in the dedicated KVM practice guest, disabled ordinary-user namespace creation, and set kernel pointer restriction to 2. Regenerated the guest's initramfs, restarted only that VM, and verified persistence. The restrictions reduce exposure but do not patch kernel CVEs; future rootless container/sandbox use in this guest requires review.

All three real-time file-change tests passed again in manager and indexer with matching identifiers and hashes. All 13 original media container identities were unchanged, nine endpoint checks ended at HTTP 200, four central Wazuh services were active, and all five positive/negative lab network probes matched policy. The scanner still reported 440 kernel records, including two Critical and 111 High ratings. No findings were suppressed. No unattended updater, recurring monitor, automatic reboot, host/kernel upgrade, or backup configuration change was installed by this follow-up.

### FIM lab security review and plain-English report

Published a downloadable [plain-English project summary](https://github.com/J0N3B0I/Wazuh-FIM-Lab/blob/main/plain-english-summary.pdf) and [security review](https://github.com/J0N3B0I/Wazuh-FIM-Lab/blob/main/docs/security-review.md).

Refreshed Ubuntu metadata and upgraded 67 lab packages, installing six new packages. Rebooted only the lab onto kernel `6.8.0-151-generic`, then removed the obsolete kernel packages. Root and password SSH login are disabled. The enrollment socket is stopped and disabled, and its port was removed from the lab's guest and host allow rules. The temporary Ubuntu-only update proxy was stopped and its script removed.

Re-tested all three FIM operations in manager and indexed alerts; the observed repeat-test times were 9.83, 10.76, and 10.77 seconds. All 13 existing media container identities were unchanged, nine HTTP endpoint checks ended at 200 after redirects, and the four central Wazuh services were active. Runtime network probes confirmed event forwarding worked while enrollment, host administration, selected media access, and public HTTPS access failed as expected.

The lab's Wazuh package/CVE inventory fell from 3,335 to 440 records after synchronization. Remaining records concern the current repository-candidate kernel and include two Critical and 111 High ratings. The two Critical findings were reviewed against Ubuntu advisories and current guest usage; they remain documented, with no suppression or vulnerability-free claim. One SQLite update is deferred by Ubuntu's phased rollout. Backup work remains deferred pending storage; existing backup settings were preserved.

### Watched movie cleanup

Removed three fully watched movies following an owner-requested storage cleanup. Jellyfin had one active profile. Immediately before deletion, each selected movie was marked played, had no resume position, was not favorited, and was absent from active playback sessions. Each library file had one filesystem link. No matching download jobs or residual download copies were found.

Deleted the selected entries through Radarr with file deletion and import exclusions enabled, waited for directory removal, and refreshed Jellyfin. Verified that the other 16 Radarr records were preserved and Jellyfin's remaining movie count was 13. Available media filesystem space increased by **28.81 GiB**, reaching **151.19 GiB free** at verification.

Homarr, Jellyfin, Radarr, Sonarr, Prowlarr, Seerr, and the download client returned HTTP 200 during post-cleanup checks. Selection used fully watched status. An age-based removal cutoff remains unspecified.

### Wazuh deployment documentation

Published the dedicated [Wazuh Security Monitoring Homelab](https://github.com/J0N3B0I/Wazuh-Homelab) repository and linked it from the main project. Documentation covers the actual 4.14.8 deployment, three connected remote agents, local monitoring, Filebeat forwarding, indexing, investigation, and operations.

Read-only inspection verified four active central services, a successful Filebeat output connection test, and green indexer health. The inspection counted 49 alert indices and found no assigned ISM policy on those indices. Retention review and recovery verification remain follow-up work. Proposed detection exercises are identified as future projects.

### Completed file integrity monitoring project

Deployed a dedicated Ubuntu 24.04.5 LTS VM with 2 cores, 2 GiB RAM, and a 20 GiB thin-provisioned disk. A separate bridge, guest firewall, and scoped host forwarding provide Wazuh connectivity with no guest default route. Installed and enrolled a matching 4.14.8 agent and enabled real-time monitoring of a dedicated test directory.

Verified all three controlled file operations in manager alerts and indexed documents: creation rule 554, modification rule 550, and deletion rule 553. Hash values matched, event IDs agreed between manager and indexer, and first indexed observations were 9.76, 10.80, and 16.46 seconds after the respective operations. Targeted network checks passed, all existing media container IDs were preserved, nine application endpoint checks passed, and four central Wazuh services were active.

Published the [project summary and evidence](https://github.com/J0N3B0I/Wazuh-FIM-Lab). The test VM remains available with automatic host-boot startup disabled. Its backup coverage is outside the current job while additional storage is being obtained.

## 2026-11-11

### Media storage cleanup

Removed two user-selected movies through Radarr with file deletion and import exclusions enabled. Checked for matching active download entries and residual download files. Each library file had a single filesystem link, and no matching download copies were found.

Verified that the movie directories were removed, the other 20 Radarr movie records were preserved, and both selected entries disappeared from Jellyfin after a library refresh. Media filesystem availability increased by approximately **15.16 GiB**, reaching **128.22 GiB free** at verification. Homarr, Jellyfin, Radarr, Sonarr, Prowlarr, Seerr, and the download client responded to their health or web checks.

Removal was explicitly requested by the owner. Import exclusions prevent automatic re-imports through Radarr lists.

### Additional requested media removal

After title clarification, removed one further owner-selected movie through Radarr with file deletion and an import exclusion. Verified that the file and Jellyfin catalog entry were removed and the other 19 Radarr movie records were preserved. The operation recovered approximately **4.17 GiB**, leaving **132.18 GiB free** on the media filesystem. All nine tested service endpoints returned HTTP 200 afterward.

### Engineering report

Published the [six-page engineering report](reports/2026-11-11/README.md) with PDF, HTML, Markdown, a service architecture overview, and verified maintenance outcomes. Fresh availability checks found 13 running Docker containers and nine responding endpoints. Proxmox task history confirmed that the November 10 and 11 guest backup jobs were refused by the capacity guard, with November 9 the latest successful job in the inspected history.
