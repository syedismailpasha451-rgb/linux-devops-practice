**🟦 LEVEL–1 BASIC FILES**
📄 level-1-basic/user-management/create_users.sh
#!/bin/bash

groupadd devteam

useradd -m -s /bin/bash -G devteam dev1
echo "dev1:DevPass123" | chpasswd

useradd -m -s /bin/bash -G devteam dev2
echo "dev2:DevPass123" | chpasswd

echo "Users and group created successfully."


📄 level-1-basic/user-management/permissions.sh


#!/bin/bash

mkdir -p /opt/myapp
chown :devteam /opt/myapp
chmod 770 /opt/myapp

echo "Permissions updated for /opt/myapp"

📄 level-1-basic/package-installation/install_packages.sh
#!/bin/bash

apt update
apt install -y git nginx default-jdk

echo "Packages installed: git, nginx, java"

📄 level-1-basic/system-info/system_info.sh
#!/bin/bash

echo "CPU Info:"
lscpu

echo "Memory:"
free -h

echo "Disk Storage:"
df -h

echo "OS Version:"
cat /etc/os-release

📄 level-1-basic/README.md
# Level 1 – Basic Linux Tasks

This section covers foundational Linux administration tasks:
- User & group creation
- File/directory permissions
- Installing packages
- Checking system information

🟩 LEVEL–2 INTERMEDIATE FILES
📄 level-2-intermediate/cron-backups/backup_script.sh
#!/bin/bash

tar -czf /opt/myapp_backup_$(date +%F).tar.gz /opt/myapp

echo "Backup created in /opt"

📄 level-2-intermediate/shell-scripts/log_cleanup.sh
#!/bin/bash

find /var/log -type f -name "*.log" -mtime +7 -exec rm -f {} \;

echo "Old logs cleaned successfully."

📄 level-2-intermediate/shell-scripts/restart_service.sh
#!/bin/bash

systemctl restart nginx
systemctl status nginx

📄 level-2-intermediate/shell-scripts/health_check.sh
#!/bin/bash

curl -I http://localhost

📄 level-2-intermediate/log-management/log_commands.txt
ls -lh /var/log
tail -f /var/log/syslog
tail -f /var/log/nginx/access.log
tail -f /var/log/nginx/error.log

📄 level-2-intermediate/system-monitoring/monitoring_commands.txt
top
htop
vmstat 1
iostat
ss -tulnp
journalctl -u nginx

📄 level-2-intermediate/README.md
# Level 2 – Intermediate DevOps Tasks

Includes:
- Cron backups
- Shell scripts for automation
- Log management
- Monitoring Linux servers

🟥 LEVEL–3 ADVANCED FILES
📄 level-3-advanced/systemd-service/myapp.service
[Unit]
Description=My Java Application
After=network.target

[Service]
User=root
ExecStart=/usr/bin/java -jar /opt/myapp/app.jar
Restart=always

[Install]
WantedBy=multi-user.target

📄 level-3-advanced/ssh-hardening/ssh_config_hardening.txt
PermitRootLogin no
PasswordAuthentication no
AllowUsers dev1 dev2

📄 level-3-advanced/lvm-setup/lvm_commands.txt
pvcreate /dev/sdb
vgcreate data_vg /dev/sdb
lvcreate -L 5G -n app_lv data_vg
mkfs.ext4 /dev/data_vg/app_lv
mkdir /mnt/appdata
mount /dev/data_vg/app_lv /mnt/appdata

📄 level-3-advanced/firewall-setup/firewall_rules.txt
ufw allow 22
ufw allow 80
ufw allow 443
ufw enable
ufw status

📄 level-3-advanced/logrotate/myapp_logrotate.conf
/opt/myapp/logs/*.log {
    daily
    rotate 7
    compress
    notifempty
    missingok
}

📄 level-3-advanced/README.md
# Level 3 – Advanced Linux Administration

Production-level tasks:
- Systemd service
- SSH hardening
- LVM
- Firewall
- Logrotate

🟦 ALL-IN-ONE INSTALLATION SCRIPT
📄 scripts/all-in-one-setup.sh
#!/bin/bash

echo "Creating users..."
groupadd devteam
useradd -m -s /bin/bash -G devteam dev1
useradd -m -s /bin/bash -G devteam dev2

echo "Setting up directory..."
mkdir -p /opt/myapp
chown :devteam /opt/myapp
chmod 770 /opt/myapp

echo "Installing packages..."
apt update
apt install -y git nginx default-jdk

echo "Setup completed successfully."

📄 scripts/README.md
# Automation Scripts

This folder contains full server setup automation scripts.

🏆 MAIN README.md
📄 README.md
# Linux DevOps Practice – Server Automation

This repository contains full Linux automation tasks used in real-world DevOps projects.

## Levels Covered

### ✔️ Level 1 – Basic  
- User management  
- Permissions  
- Package installation  
- System information  

### ✔️ Level 2 – Intermediate  
- Cron backups  
- Shell scripting  
- Log management  
- Server monitoring  

### ✔️ Level 3 – Advanced  
- Systemd services  
- SSH hardening  
- LVM management  
- Firewall rules  
- Logrotate  

🎉 DONE!






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








