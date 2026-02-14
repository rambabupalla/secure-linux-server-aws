# Secure Linux Server Deployment & Hardening on AWS EC2

## Project Overview
This project demonstrates deployment and security hardening of an Ubuntu Linux server on AWS EC2.

The goal was to implement production-level SSH security, user privilege management, firewall configuration, and intrusion prevention.

---

## Technologies Used
- AWS EC2
- Ubuntu 22.04
- SSH
- UFW Firewall
- Fail2Ban

---

## Project Implementation Steps

### 1. EC2 Deployment
- Launched Ubuntu EC2 instance on AWS
- Configured Security Group to allow SSH (Port 22)
- Connected via SSH using key-based authentication

### 2. User Management
- Created dedicated admin user
- Configured sudo privileges
- Disabled direct root login

### 3. SSH Hardening
- Disabled root login
- Disabled password authentication
- Restricted SSH access to specific user using `AllowUsers`
- Verified configuration safely using `sshd -t`

### 4. Firewall Configuration (UFW)
- Installed UFW
- Allowed only required ports (22)
- Enabled firewall
- Verified active rules

### 5. Intrusion Prevention (Fail2Ban)
- Installed Fail2Ban
- Enabled SSH jail
- Configured retry limits and ban time
- Verified jail status

---

## Security Measures Implemented
- Principle of Least Privilege
- Key-based authentication
- Access restriction using AllowUsers
- Firewall-based port control
- Automated brute-force attack protection

---

## Screenshots
Screenshots of implementation steps are available in the `/screenshots` folder.

---

## Outcome
A production-ready secure Linux server with hardened SSH, firewall protection, and intrusion prevention.

---

## Author
Rambabu
