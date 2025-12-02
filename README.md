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





🚀 Next Step

If you want, I can also create:

✅ Each LEVEL_x.md file content
✅ Full automation bash scripts
✅ A complete FULL_ROADMAP.md
✅ A professional GitHub project description

Just say: “Create all roadmap files” or “Create bash scripts also”.

You said:
create a bash scripts also
ChatGPT said:

Perfect, Syed!
Below are production-ready Bash automation scripts for your repository.
These match your Level 1 → Level 3 roadmap and are written clean, professional, and fully executable.

You can copy each script into your:

linux-devops-practice/scripts/

✅ 1. install_packages.sh

Installs Git, Nginx, Java, updates system.

#!/bin/bash

set -e

echo "🔄 Updating system..."
sudo apt update -y

echo "📦 Installing packages: git, nginx, openjdk-17..."
sudo apt install -y git nginx openjdk-17-jdk

echo "✔️ Packages installed successfully."

✅ 2. set_users_groups.sh

Creates DevOps users + group and sets permissions.

#!/bin/bash

set -e

GROUP="devteam"
USERS=("dev1" "dev2" "dev3")

echo "👥 Creating group: $GROUP"
sudo groupadd -f $GROUP

echo "👤 Creating users & adding to group..."
for user in "${USERS[@]}"; do
    if id "$user" &>/dev/null; then
        echo "User $user already exists."
    else
        sudo useradd -m -s /bin/bash -G $GROUP $user
        echo "User $user created."
    fi
done

echo "📁 Setting project permissions..."
sudo mkdir -p /project/app
sudo chown -R :$GROUP /project/app
sudo chmod -R 2775 /project/app

echo "✔️ Users, groups & permissions completed."

✅ 3. backup_cron.sh

Automates daily backup using cron job.

#!/bin/bash

set -e

SOURCE="/project/app"
BACKUP="/backup/app_$(date +%F).tar.gz"

echo "📦 Taking backup..."
sudo tar -czf $BACKUP $SOURCE

echo "Backup created at: $BACKUP"

echo "⏰ Setting cron job for daily backups..."
CRON_JOB="0 2 * * * tar -czf /backup/app_\$(date +\%F).tar.gz /project/app"

(crontab -l 2>/dev/null; echo "$CRON_JOB") | crontab -

echo "✔️ Daily backup cron configured."

✅ 4. cleanup_logs.sh

Deletes logs older than 7 days.

#!/bin/bash

set -e

LOG_DIR="/var/log"
DAYS=7

echo "🧹 Cleaning logs older than $DAYS days in $LOG_DIR..."
sudo find $LOG_DIR -type f -mtime +$DAYS -exec rm -f {} \;

echo "✔️ Old logs cleaned."

✅ 5. service_health_check.sh

Checks if nginx, ssh, cron services are running.

#!/bin/bash

SERVICES=("nginx" "ssh" "cron")

echo "⚕️ Checking system services..."

for svc in "${SERVICES[@]}"; do
    if systemctl is-active --quiet "$svc"; then
        echo "✔️ $svc is running"
    else
        echo "❌ $svc is NOT running — restarting..."
        sudo systemctl restart "$svc"
    fi
done

✅ 6. create_systemd_service.sh

Creates a custom systemd service.

#!/bin/bash

set -e

SERVICE_NAME="myapp"
APP_PATH="/project/app/start.sh"

echo "⚙️ Creating systemd service: $SERVICE_NAME"

sudo bash -c "cat > /etc/systemd/system/$SERVICE_NAME.service <<EOF
[Unit]
Description=My Custom App Service
After=network.target

[Service]
ExecStart=$APP_PATH
Restart=always
User=root

[Install]
WantedBy=multi-user.target
EOF"

sudo systemctl daemon-reload
sudo systemctl enable $SERVICE_NAME

echo "✔️ systemd service created & enabled."

✅ 7. harden_ssh.sh

Secures SSH for production.

#!/bin/bash

set -e

echo "🔐 Hardening SSH..."

sudo sed -i 's/#PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config

sudo systemctl restart sshd

echo "✔️ SSH security applied."

✅ 8. firewall_rules.sh

Enables and configures UFW firewall.

#!/bin/bash

set -e

echo "🔥 Configuring firewall rules..."

sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable

echo "✔️ Firewall configured."

✅ 9. lvm_setup.sh

Creates LVM physical volume → volume group → logical volume.

#!/bin/bash

set -e

DISK="/dev/sdb"
VG="vgdata"
LV="lvdata"

echo "💽 Creating physical volume..."
sudo pvcreate $DISK

echo "📦 Creating volume group: $VG"
sudo vgcreate $VG $DISK

echo "📏 Creating logical volume: $LV"
sudo lvcreate -l 100%FREE -n $LV $VG

echo "📂 Formatting & mounting..."
sudo mkfs.ext4 /dev/$VG/$LV
sudo mkdir -p /mnt/data
sudo mount /dev/$VG/$LV /mnt/data

echo "✔️ LVM setup completed."

✅ 10. logrotate_app.sh

Creates log rotation for your app.

#!/bin/bash

set -e

echo "🔄 Setting up logrotate for app logs..."

sudo bash -c "cat > /etc/logrotate.d/myapp <<EOF
/project/app/logs/*.log {
    daily
    rotate 7
    compress
    missingok
    notifempty
}
EOF"

echo "✔️ Logrotate configured."








