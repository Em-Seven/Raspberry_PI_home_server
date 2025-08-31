# Raspberry Pi Home Server Project

This repository documents my personal Raspberry Pi home server setup and the configurations I used to build it. 
The project focuses on learning Linux, improving IT administration skills, and building a secure and functional server environment.

---

## Features Implemented
- **SSH Hardening**  
  - Configured SSH keys for authentication
    - [sshd_config.md](Configs/sshd_config.md)
  - Disabled root login  
  - Changed default port  
  - Fail2Ban + UFW firewall rules
    - [Fail2Ban_jail.local.md](Configs/Fail2Ban_jail.local.md)
    - [UFW_rules.md](Configs/UFW_rules.md)
  - Remote access via Tailscale  

- **System Maintenance**  
  - Automatic security updates with email notifications
    - [unattended-upgrades.md](Configs/unattended-upgrades.md)
  - Custom hostname  
  - Monitoring with journalctl for system logs, troubleshooting, and service tracking


- **File Management**  
  - SFTP access  
  - File Browser web application
      - [Web_file_browser.png](Assets/Web_file_browser.png)

- **Monitoring**  
  - Netdata for real-time system metrics
     - [Netdata.png](Assets/Netdata.png)

- **Storage & Mounting**
  - Configured an external USB drive for persistent data storage
  - Automated daily backups using rsync  
    
    


- **Web Hosting** - Nginx setup for serving websites and apps
  - **Laravel Framework Integration**
    - First page deployment
    - Custom route configuration
    - MVC architecture understanding (Model, View, Controller)
  - **Live Site**: [The 7pi Laboratory](http://7pi-labs.tech) 
			- [7pi-labs.png](Assets/7pi-labs.png)
  - **DNS & Traffic Management**
    - Cloudflare Tunnel setup for secure, public access
  - **Laravel Maintenance**
    - composer.json & composer.lock for dependency management



---

## Purpose
The goal of this project is to use the Raspberry Pi as a Linux-based environment to practice server administration, system security, automation, and monitoring — skills relevant for IT roles.

---

## Project Log
For detailed step-by-step progress and notes, see:  
📄 [PROJECT_LOG.md](./PROJECT_LOG.md)

---


## Future Plans
- Host lightweight services (e.g., wiki, dashboard)  
- Expand monitoring and backups  

---

## Languages
-  English

---

## Configuration Files

The configs/ directory contains **example versions** of the configuration files used in this project.  

- All sensitive information (e.g., IP addresses, credentials, email accounts) has been **sanitized**.  
- Placeholders are included so that anyone reviewing the repository can **understand the changes** made.  
- These files are provided for **documentation and reproducibility** purposes, not for direct deployment.  

The actual production-ready configurations are stored securely and are **not part of this repository**.

---

![Linux](https://img.shields.io/badge/OS-Linux-blue?logo=linux&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/Hardware-Raspberry%20Pi-red?logo=raspberrypi&logoColor=white)
![Security](https://img.shields.io/badge/Focus-Security-green?logo=datadog&logoColor=white)
![Automation](https://img.shields.io/badge/Focus-Automation-yellow?logo=gnubash&logoColor=white)
![Monitoring](https://img.shields.io/badge/Focus-Monitoring-orange?logo=prometheus&logoColor=white)
![Server](https://img.shields.io/badge/Role-Server-grey?logo=serverfault&logoColor=white)
![DevOps Basics](https://img.shields.io/badge/Path-DevOps%20Basics-blueviolet?logo=githubactions&logoColor=white)




