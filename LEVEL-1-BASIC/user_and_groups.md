\# User \& Group Management (Linux)



\## Create a Group

groupadd devteam



\## Create Users and Assign to Group

useradd -m -s /bin/bash -g devteam syed

useradd -m -s /bin/bash -g devteam tanveer



\## Set Password for Users

passwd syed

passwd tanveer



\## List Users \& Groups

cat /etc/passwd

cat /etc/group



\## Check Group of a User

id syed



