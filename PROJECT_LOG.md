# Project Log – Raspberry Pi Linux Server

This file documents the steps, configurations, and services set up on my Raspberry Pi to build a secure and functional home server.

---

## Security & Access
- Configured **SSH key authentication** (disabled password login).
- Changed default hostname (not using "raspberry").
- Disabled root login for SSH.
- Restricted SSH access to a **non-default port**.
- Enabled **UFW firewall** with minimal open ports.
- Installed and configured **Fail2Ban** to block brute-force attempts.
- Remote access from outside home network is only allowed via **Tailscale VPN**.

---

## System Maintenance
- Enabled **automatic security updates** via `unattended-upgrades`.
- Configured system to send an **email notification** after updates (via Gmail SMTP relay).
- Set up **journalctl log management**:
  - Persistent logging enabled (`/var/log/journal`).
  - Limited log size with `SystemMaxUse` in `journald.conf`.
  - Logs rotated automatically to prevent SD card from filling up.
  - Tested log access with `journalctl -xe` and boot logs with `journalctl -b`.

---

## File Management
- Enabled **SFTP** for secure file transfer (restricted to SSH key users).
- Installed and configured **FileBrowser** as a web-based file manager.
- Set FileBrowser to **start automatically on boot**.

---

## Monitoring & Observability
- Installed **Netdata** for real-time system monitoring (CPU, RAM, network, services).
- Configured Netdata to run as a service.

---

## External Disk Mounting
-The disk is automatically mounted at boot using /etc/fstab.

---

## Notes
- All services are configured to run on boot.
- Configurations have been tested and verified.
- Further improvements planned:  
  - Nginx reverse proxy setup for secure HTTPS access.  
  - Backups of configurations and data.

---
