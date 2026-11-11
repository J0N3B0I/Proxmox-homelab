# Media stack migration

The media services originally ran as native Linux services inside a Proxmox LXC. The migration moved Jellyfin, Radarr, Sonarr, Prowlarr, and qBittorrent into Docker Compose in the same LXC. Wazuh runs in a separate VM.

## Cutover and validation

1. Take a Proxmox snapshot before the migration and record where the original applications store their data.
2. Configure the Docker stack with application data under a dedicated directory and a shared media filesystem. Keep the download and library paths on the same filesystem where hardlinks are required.
3. Disable the retired native units and validate playback, requests, and the download client through the Docker services.
4. Check private access through Tailscale. The unprivileged media LXC uses TUN device passthrough so Tailscale can run inside it.

## Retiring the original installations

Before removing the native applications, inspect the running Docker containers' bind mounts and compare them with the native service paths. Confirm the old units are inactive and preview package removal to verify which packages will be removed.

In this lab, Docker used dedicated application data directories and the shared media mount. The retired binaries, native service definitions, and unused data directories could therefore be removed independently. The cleanup recovered **1.22 GiB** on the LXC system filesystem. All 13 Docker containers stayed running, and the service checks passed after cleanup.

The pre-migration snapshot was retained. A snapshot can still reference blocks that were removed from the active filesystem, so the space recovered inside the LXC can differ from the space recovered on the Proxmox storage pool.
