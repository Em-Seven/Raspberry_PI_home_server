# UFW Firewall Configuration - Raspberry Pi Server Setup

## Base Rules
```bash
# Reset rules (if needed)
sudo ufw --force reset

# Default policies
sudo ufw default deny incoming
sudo ufw default allow outgoing

# SSH (custom port XXXX - same as SSH config)
sudo ufw allow XXXX/tcp comment 'SSH Custom Port'
sudo ufw limit XXXX/tcp comment 'SSH Rate Limiting'

# Tailscale (VPN overlay network)
sudo ufw allow XXXX/udp comment 'Tailscale'

# SFTP (uses SSH port)
# Web File Browser (if using default port)
sudo ufw allow XXXX/tcp comment 'HTTP'
sudo ufw allow XXXX/tcp comment 'HTTPS'

# Netdata Monitoring
sudo ufw allow XXXX/tcp comment 'Netdata'
