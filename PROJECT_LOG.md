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
- Enabled **automatic security updates** via unattended-upgrades.
- Configured system to send an **email notification** after updates (via Gmail SMTP relay).
- Set up **journalctl log management**:
  - Persistent logging enabled (/var/log/journal).
  - Limited log size with SystemMaxUse in journald.conf.
  - Logs rotated automatically to prevent SD card from filling up.
  - Tested log access with journalctl -xe and boot logs with journalctl -b.

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

## Storage & Mounting
- The disk is automatically mounted at boot using /etc/fstab.
- Backups:  
  - Automated daily backups using rsync  
  - Covers:
    - Home directories  
    - System configuration files  
    - System logs  
  - Stored safely on external USB drive  
  - Automated with cron job

---

### Web Hosting & Application Deployment

#### Nginx Web Server
- Configured Nginx as the primary web server.
- Set up a **Server Block** to serve a Laravel application from the `/var/www` directory.
- Implemented an Nginx reverse proxy for Netdata, allowing access through a subdomain.

#### Laravel Framework Integration
- Installed **PHP**, **Composer**, and the **Laravel framework**.
- Deployed the initial **"Under Construction"** landing page.
- Practiced and understood core concepts of the **MVC architecture** (Model, View, Controller), routes, and the **Blade templating engine**.
- Integrated initial **comment system** using Blade templates and SQLite database for practice.
- Set up basic **routes** and **layouts** to structure the first version of the site.
- Learned hands-on Laravel deployment and local web hosting using Nginx.

#### Secure Public Access with Cloudflare Tunnel
- Deployed a **Cloudflare Tunnel** to securely expose the Nginx web server to the internet without opening any firewall ports.
- Provides automated **HTTPS encryption** and **DDoS protection**.

### Docker & Laravel Setup
- Installed Docker and Docker Compose on Raspberry Pi  
  - `sudo apt update && sudo apt install docker.io docker-compose -y`  
  - Enabled Docker service: `sudo systemctl enable --now docker`  
  - Added user to Docker group: `sudo usermod -aG docker $USER`  

- Containers used:  
  - **laravel_app** → PHP + Laravel  
  - **laravel_nginx** → Nginx web server  

- Volumes:  
  - `.:/var/www/my_laravel_app` → live project files  
  - `/mnt/usb:/mnt/usb` → persistent storage for backups  

- Start containers: `docker compose up -d --build`  
- Useful commands:  
  - `docker compose ps` → list running containers  
  - `docker compose logs -f` → tail logs  
  - `docker compose exec app bash` → enter Laravel container  
  - `docker compose exec nginx bash` → enter Nginx container  
  - `docker compose down` → stop containers  

### Backup Workflow
- Backup script: `/var/www/my_laravel_app/scripts/backup.sh`  
- Backup destination: `/mnt/usb/laravel_backups`  
- Run manually inside container: `bash /var/www/my_laravel_app/scripts/backup.sh`  
- Automate with cron:  
  - `0 3 * * * /var/www/my_laravel_app/scripts/backup.sh`  
- Notes:  
  - All Laravel files visible on host via volume mounts  
  - Containers are ephemeral, but volumes persist data  
  - Install tools inside container if missing (e.g., `vim`, `rsync`) in Dockerfile or manually

---

## Notes
- All services are configured to run on boot.
- Configurations have been tested and verified.
- Future Plans
	- Deploy the full website: Replace the "Under Construction" page with a full, functional website.
	- Database integration: Set up a database (e.g., SQLite or MySQL) and connect it to the Laravel application.
	- User authentication: Implement a user login system to secure parts of the website.
	- Further automation: Create a script for automatic updates of the Laravel application.

---
