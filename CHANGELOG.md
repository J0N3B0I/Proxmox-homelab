# Homelab change log

## 2026-11-11

### Media storage cleanup

Removed two user-selected movies through Radarr with file deletion and import exclusions enabled. Checked for matching active download entries and residual download files. Each library file had a single filesystem link, and no matching download copies were found.

Verified that the movie directories were removed, the other 20 Radarr movie records were preserved, and both selected entries disappeared from Jellyfin after a library refresh. Media filesystem availability increased by approximately **15.16 GiB**, reaching **128.22 GiB free** at verification. Homarr, Jellyfin, Radarr, Sonarr, Prowlarr, Seerr, and the download client responded to their health or web checks.

Removal was explicitly requested by the owner. Import exclusions prevent automatic re-imports through Radarr lists.
