# Commands Used – Secure Linux Server Deployment & Hardening

## 1. System Update
sudo apt update
sudo apt upgrade -y

---

## 2. User Management

# Create new admin user
sudo adduser linux-admin

# Add user to sudo group
sudo usermod -aG sudo linux-admin

# Verify user groups
groups linux-admin

# Switch to new user
sudo su - linux-admin

# Check user identity
whoami
id

---

## 3. Configure SSH Key for New User

# Create .ssh directory
sudo mkdir -p /home/linux-admin/.ssh

# Copy authorized keys from ubuntu user
sudo cp /home/ubuntu/.ssh/authorized_keys /home/linux-admin/.ssh/

# Set correct ownership
sudo chown -R linux-admin:linux-admin /home/linux-admin/.ssh

# Set correct permissions
sudo chmod 700 /home/linux-admin/.ssh
sudo chmod 600 /home/linux-admin/.ssh/authorized_keys

---

## 4. SSH Hardening

# Open SSH configuration file
sudo nano /etc/ssh/sshd_config

# Validate SSH configuration
sudo sshd -t

# Restart SSH service
sudo systemctl restart ssh

# Verify SSH service
sudo systemctl status ssh

# Verify hardening settings
sudo cat /etc/ssh/sshd_config | grep -E "PermitRootLogin|PasswordAuthentication|AllowUsers"

---

## 5. Firewall Configuration (UFW)

# Install UFW
sudo apt install ufw -y

# Allow SSH port
sudo ufw allow 22

# Enable firewall
sudo ufw enable

# Check firewall status
sudo ufw status verbose

---

## 6. Fail2Ban Installation & Configuration

# Install Fail2Ban
sudo apt install fail2ban -y

# Copy default config to local config
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local

# Edit jail configuration
sudo nano /etc/fail2ban/jail.local

# Restart Fail2Ban
sudo systemctl restart fail2ban

# Check Fail2Ban status
sudo fail2ban-client status
sudo fail2ban-client status sshd

# View Fail2Ban logs
sudo journalctl -u fail2ban --no-pager | tail -20

---

## 7. Log Monitoring

# Monitor authentication logs
sudo tail -f /var/log/auth.log
