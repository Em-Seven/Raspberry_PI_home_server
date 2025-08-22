# SSH Configuration - Raspberry Pi Server Setup

## Secure SSH Setup

### Main Configuration (`/etc/ssh/sshd_config`)
```bash
# Custom SSH Port (change XXXX to your chosen port)
Port XXXX

# Security Settings
PermitRootLogin no
MaxAuthTries 3
LoginGraceTime 1m
ClientAliveInterval 300
ClientAliveCountMax 2

# Key Authentication
PubkeyAuthentication yes
PasswordAuthentication no
ChallengeResponseAuthentication no

# Restrict users (add your username)
AllowUsers your_username

# Additional security
UsePAM yes
X11Forwarding no
PrintMotd no
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
