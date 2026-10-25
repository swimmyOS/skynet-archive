# skynet-archive

Configuration snapshots of skynet, the Raspberry Pi that hosts the homelab's file shares, Jellyfin media server and Pi-hole DNS filter.

The files record the host's actual configuration at a point in time. Each update is committed, so the Git history serves as a record of changes. The initial commit is the January 2026 baseline, taken before the network was segmented into VLANs.

## Contents

- `docs/state/mounts.txt`: NAS storage mount, from `findmnt`
- `docs/state/samba-config.txt`: effective Samba configuration, from `testparm -s`
- `docs/state/ufw-rules.txt`: host firewall status

Usernames in the snapshots are replaced with `<nas-user>`.

## Current State (October 2026)

Storage is a single ext4 volume mounted at `/srv/nas` with `noatime`, which avoids a disk write each time a file is read.

Samba provides three shares, Shared, Backups and Media, all of which require authentication.

No host firewall is installed. UFW was removed after skynet moved to a dedicated server VLAN. The network firewall permits only specific services from the trusted network and blocks the server VLAN from initiating connections to other devices.

## Related Repositories

- [rpi-nas-media-server](https://github.com/swimmyOS/rpi-nas-media-server): service configuration on the Pi
- [homelab-network-documentation](https://github.com/swimmyOS/homelab-network-documentation): network design

## Author

Joseph Leahy Jr.  
IT & Cybersecurity  
https://www.linkedin.com/in/joseph-l-904673159
