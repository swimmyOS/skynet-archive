# skynet Archive

Point-in-time snapshots of the configuration on **skynet**, the Raspberry Pi that serves as my NAS, media server and DNS filter.
Each snapshot records how the host is actually set up, so changes can be compared over time and the system can be rebuilt from a known state.

---

## Contents

| File | What it captures |
| --- | --- |
| `docs/state/mounts.txt` | How the NAS storage is mounted |
| `docs/state/samba-config.txt` | The effective Samba configuration and shares |
| `docs/state/ufw-rules.txt` | Host firewall status |

The files show the current state. Earlier snapshots are kept in the Git history, starting with the January 2026 baseline taken before the network was segmented.

---

## Current State

- **Storage:** a single EXT4 volume mounted at `/srv/nas`, with `noatime` to reduce disk writes
- **File sharing:** three authenticated shares (Shared, Backups, Media) plus per-user home directories; guest access is not offered on any share
- **Firewall:** no host firewall; the network firewall allows only specific services from the trusted zone and blocks the server zone from starting connections to client devices

---

## Capturing a Snapshot

Run on skynet, then copy each output into its file:

```bash
findmnt -o TARGET,SOURCE,FSTYPE,OPTIONS /srv/nas
testparm -s
```

Before committing, replace usernames with placeholders such as `<nas-user>`, and leave out addresses or anything else that identifies the network.

---

## Related Repositories

- **Raspberry Pi NAS & Media Server:** how the services on this host are configured  
  https://github.com/swimmyOS/rpi-nas-media-server
- **Homelab Network Infrastructure:** the network this host sits on  
  https://github.com/swimmyOS/homelab-network-documentation

---

## Author

Joseph Leahy Jr.  
IT & Cybersecurity  
https://www.linkedin.com/in/joseph-l-904673159
