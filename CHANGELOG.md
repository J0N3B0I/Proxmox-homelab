# Homelab change log

## 2026-11-11

### Media storage cleanup

Removed two user-selected movies through Radarr with file deletion and import exclusions enabled. Checked for matching active download entries and residual download files. Each library file had a single filesystem link, and no matching download copies were found.

Verified that the movie directories were removed, the other 20 Radarr movie records were preserved, and both selected entries disappeared from Jellyfin after a library refresh. Media filesystem availability increased by approximately **15.16 GiB**, reaching **128.22 GiB free** at verification. Homarr, Jellyfin, Radarr, Sonarr, Prowlarr, Seerr, and the download client responded to their health or web checks.

Removal was explicitly requested by the owner. Import exclusions prevent automatic re-imports through Radarr lists.

### Additional requested media removal

After title clarification, removed one further owner-selected movie through Radarr with file deletion and an import exclusion. Verified that the file and Jellyfin catalog entry were removed and the other 19 Radarr movie records were preserved. The operation recovered approximately **4.17 GiB**, leaving **132.18 GiB free** on the media filesystem. All nine tested service endpoints returned HTTP 200 afterward.

### Engineering report

Published the [six-page engineering report](reports/2026-11-11/README.md) with PDF, HTML, Markdown, a service architecture overview, and verified maintenance outcomes. Fresh availability checks found 13 running Docker containers and nine responding endpoints. Proxmox task history confirmed that the November 10 and 11 guest backup jobs were refused by the capacity guard, with November 9 the latest successful job in the inspected history.
