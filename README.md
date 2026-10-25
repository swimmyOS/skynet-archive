# skynet-archive

Config snapshots from skynet, the Raspberry Pi in my homelab that runs my file shares, Jellyfin and Pi-hole.

I keep these so I have a record of how the box is actually set up, not just how I remember setting it up. When something changes I grab the files again and commit them, so the Git history works as a changelog. The first commit is the baseline from January 2026, before I split my network into VLANs.

## What's here

- `docs/state/mounts.txt`: how the NAS drive is mounted
- `docs/state/samba-config.txt`: the Samba config as Samba actually reads it
- `docs/state/ufw-rules.txt`: firewall status on the Pi

## Where things stand (October 2026)

The NAS is a single ext4 drive mounted at `/srv/nas`. I switched it to `noatime` so the drive isn't writing a timestamp every time something gets read.

Samba has three shares (Shared, Backups and Media), and all of them need a login.

There's no firewall on the Pi anymore. I removed UFW after moving skynet onto its own server VLAN, since the main firewall already controls what can reach it: only a handful of services from my trusted network, and nothing on the server VLAN can open connections back to my other devices.

## Updating it

On skynet:

```bash
findmnt -o TARGET,SOURCE,FSTYPE,OPTIONS /srv/nas
testparm -s
```

Then paste the output into the matching file. This repo is public, so I swap my username for `<nas-user>` before committing.

## See also

- [rpi-nas-media-server](https://github.com/swimmyOS/rpi-nas-media-server): how the services on the Pi are set up
- [homelab-network-documentation](https://github.com/swimmyOS/homelab-network-documentation): the network around it

Joseph Leahy Jr. · [LinkedIn](https://www.linkedin.com/in/joseph-l-904673159)
