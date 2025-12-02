\# File \& Directory Permissions



\## Create Project Directory

mkdir -p /opt/myapp



\## Change Ownership to Group

chown -R :devteam /opt/myapp



\## Set Read/Write/Execute for User \& Group

chmod -R 770 /opt/myapp



\## Check Permissions

ls -l /opt/myapp



\## Change Owner

chown syed:syed /opt/myapp

