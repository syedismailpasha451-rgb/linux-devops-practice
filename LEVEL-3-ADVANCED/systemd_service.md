\# Creating a systemd Service in Linux



\## Create Service File

nano /etc/systemd/system/myapp.service



\[Unit]

Description=My Application Service

After=network.target



\[Service]

User=syed

ExecStart=/usr/bin/java -jar /opt/myapp/app.jar

Restart=always



\[Install]

WantedBy=multi-user.target



\## Reload systemd

systemctl daemon-reload



\## Start Service

systemctl start myapp



\## Enable Service at Boot

systemctl enable myapp



\## Check Status

systemctl status myapp



