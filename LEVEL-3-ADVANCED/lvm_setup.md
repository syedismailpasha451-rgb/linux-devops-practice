\# LVM Setup in Linux



\## Create Physical Volume

pvcreate /dev/sdb1



\## Create Volume Group

vgcreate data\_vg /dev/sdb1



\## Create Logical Volume

lvcreate -L 5G -n data\_lv data\_vg



\## Format the Volume

mkfs.ext4 /dev/data\_vg/data\_lv



\## Create Mount Directory

mkdir /data



\## Mount the Volume

mount /dev/data\_vg/data\_lv /data



\## Make Mount Permanent

nano /etc/fstab

/dev/data\_vg/data\_lv   /data   ext4    defaults    0 0



