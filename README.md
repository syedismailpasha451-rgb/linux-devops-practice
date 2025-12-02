```bash
linux-server-automation/
├── README.md
│
├── ROADMAP/
│   ├── LEVEL_1_BASIC.md
│   ├── LEVEL_2_INTERMEDIATE.md
│   ├── LEVEL_3_ADVANCED.md
│   └── FULL_ROADMAP.md
│
├── scripts/
│   ├── FULL_PROCEDURE.sh
│   ├── install_packages.sh
│   ├── backup_myapp.sh
│   ├── cleanup_logs.sh
│   ├── health_check.sh
│   ├── restart_myapp.sh
│   └── utils/
│       ├── colors.sh
│       └── notifications.sh
│
├── systemd/
│   └── myapp.service
│
├── logrotate/
│   └── myapp
│
├── cron/
│   ├── backup_cron.txt
│   ├── cleanup_cron.txt
│   └── healthcheck_cron.txt
│
├── ssh/
│   ├── sshd_hardening.md
│   └── fail2ban_setup.md
│
├── firewall/
│   ├── ufw_rules.md
│   └── iptables_rules.md
│
├── lvm/
│   ├── lvm_setup.md
│   └── lvm_extend_volume.md
│
├── monitoring/
│   ├── top_commands.md
│   ├── log_monitoring.md
│   └── system_audit.md
│
├── networking/
│   ├── linux_network_basics.md
│   └── troubleshooting.md
│
├── security/
│   ├── permissions_guide.md
│   └── audit_scripts.sh
│
├── assets/
│   ├── diagrams.png
│   ├── lvm_architecture.png
│   └── systemd_flow.png
│
└── examples/
    ├── nginx/
    │   └── nginx.conf
    ├── apache/
    │   └── httpd.conf
    └── sample_logs/
        └── myapp.log
```






🔰 INTRODUCTION

“Assalamualaikum everyone,
In this video, I will explain my Linux Server Automation Project where I automated a complete DevOps server setup using a single script called FULL_PROCEDURE.sh.

This script covers Level 1 to Level 3 real-time DevOps tasks.”

🔹 1. Users & Groups Automation

“In the first section, I automatically create a DevOps group and 3 developer users.
This is useful when onboarding new teams in a company.
The script checks if the user exists—if not, it creates the user and adds them to the group.”

🔹 2. Directory Permissions

“Next, I create a project directory at /project/app and assign correct permissions using group ownership and 2775 mode.
This ensures the whole team can work on the project safely.”

🔹 3. Installing Server Packages

“In this step, I update the system and install important packages like:

Git

Nginx

Java

UFW firewall

These are commonly used in any DevOps environment.”

🔹 4. Backup Automation with Cron

“I set up a daily backup at 2 AM.
The script compresses the project folder and stores it inside /backup/.

This ensures we never lose critical application data.”

🔹 5. Log Cleanup

“I configure automatic log cleanup at 3 AM.
All old logs older than 7 days inside /var/log are removed automatically to save disk space.”

🔹 6. Service Health Check

“I check important Linux services:

nginx

ssh

cron

If any service is not running, the script automatically restarts it.”

🔹 7. SSH Hardening (Security)

“I apply security best practices by disabling:

Root login

Password authentication

Only key-based SSH is allowed, which is more secure for production servers.”

🔹 8. Firewall Configuration

“I enable UFW firewall and allow only required ports:

22 for SSH

80 for HTTP

443 for HTTPS

This protects the server from unwanted access.”

🔹 9. LVM Storage Setup

“I automate LVM setup for disk /dev/sdb:

Create Physical Volume

Create Volume Group

Create Logical Volume

Format it

Mount it

This is used in real companies for scalable storage.”

🔹 10. Logrotate Setup

“I configure logrotate for application logs so old app logs automatically rotate and compress.
This keeps logs clean and optimized.”

🔹 11. Creating a Custom Systemd Service

“I create a systemd service called myapp.service that automatically runs the application on boot.
This is the standard way to run services in production.”














