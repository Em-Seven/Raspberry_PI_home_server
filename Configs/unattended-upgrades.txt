#!/bin/bash

# 1. Unattended-upgrades
sudo tee /etc/apt/apt.conf.d/50unattended-upgrades << 'EOF'
Unattended-Upgrade::Allowed-Origins {
    "Ubuntu:noble-security";
    "Ubuntu:noble-updates";
};
Unattended-Upgrade::Mail "your-email@gmail.com";
Unattended-Upgrade::Remove-Unused-Dependencies "true";
Unattended-Upgrade::Automatic-Reboot "false";
EOF

# 2. Systemd timer
sudo tee /etc/systemd/system/unattended-upgrades.timer << 'EOF'
[Unit]
Description=Run unattended-upgrades daily

[Timer]
OnCalendar=*-*-* 03:00:00
RandomizedDelaySec=30m
Persistent=true

[Install]
WantedBy=timers.target
EOF


