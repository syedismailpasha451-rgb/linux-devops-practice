\# Logrotate Configuration for Application Logs



\## Create Logrotate Rule

nano /etc/logrotate.d/myapp



/var/log/myapp/\*.log {

&nbsp;   daily

&nbsp;   rotate 7

&nbsp;   missingok

&nbsp;   compress

&nbsp;   notifempty

&nbsp;   create 0640 syed devteam

}



\## Test Logrotate

logrotate -d /etc/logrotate.conf



