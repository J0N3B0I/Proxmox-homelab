# Operations guide

## Access the lab

Connect the client to the same Tailscale network as the media container. Replace `media.example.invalid` with your container's Tailscale address or MagicDNS name.

| Service | Example URL |
| --- | --- |
| Homarr | `http://media.example.invalid:7575` |
| Jellyfin | `http://media.example.invalid:8096` |
| Seerr | `http://media.example.invalid:5055` |
| qBittorrent | `http://media.example.invalid:8080` |

For a phone, bookmark Homarr after signing in. Use the same Jellyfin URL in the Jellyfin client.

## Check storage and backups

The media filesystem and Proxmox backup destination have separate capacity limits. Check media space in Homarr. For local guest backups, check free space on the Proxmox host and review the task log.

```sh
df -h /var/lib/vz/dump
pvesh get /nodes/NODE_NAME/tasks --typefilter vzdump --limit 5
```

Replace `NODE_NAME` with the Proxmox node name before running the second command. A capacity guard refusal means the job stopped before writing a new archive. Confirm the latest successful job and archive date in the dashboard. Track media stack configuration snapshots separately from guest archives.

## Validate a dashboard change

1. Back up the Homarr configuration and record the existing layout.
2. Check the dashboard at desktop and phone widths.
3. Test shortcuts from a Tailscale client and confirm the widgets display live data.
4. Check service health and confirm the guest backup status is current.

### Example backup incident

A nightly guest backup stopped during its preflight check. The local backup destination had **63.0 GiB available**, and the guard estimated **168.5 GiB required**. The estimate includes allocated blocks on the guest volumes, 25% headroom, and a 10 GiB reserve for the host. Existing archives use space on the destination.

Homarr's media storage card showed free space on the media filesystem, which is separate from the Proxmox backup destination. The backup card showed the failed job and the date of the latest saved archives.
