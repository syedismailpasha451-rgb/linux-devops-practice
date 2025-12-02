\# SSH Hardening for Secure Linux Server



\## Open SSH Config File

nano /etc/ssh/sshd\_config



\## Disable Root Login

PermitRootLogin no



\## Disable Password Login (Use Key Only)

PasswordAuthentication no



\## Allow Only Specific Users

AllowUsers syed



\## Restart SSH Service

systemctl restart sshd



\## Check SSH Status

systemctl status sshd



