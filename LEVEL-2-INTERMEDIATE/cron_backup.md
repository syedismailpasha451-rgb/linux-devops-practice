\# Cron Backup Automation



\## Backup Script Location

/usr/local/bin/backup.sh



\## Script Content

tar -czf /backup/myapp-$(date +%F).tar.gz /opt/myapp



\## Make Script Executable

chmod +x /usr/local/bin/backup.sh



\## Add Cron Job (runs daily at 2 AM)

crontab -e



0 2 \* \* \* /usr/local/bin/backup.sh

