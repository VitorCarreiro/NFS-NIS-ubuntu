# NFS-NIS-ubuntu

NFS-NIS Config

**Install NFS server**

`apt update && apt upgrade -y && apt install nfs-kernel-server`

**Go to nano /etc/exports and place something like this choose the place you want, in my case I chose /mnt/raid5_contas**

`/mnt/raid5_contas *(rw,sync,no_subtree_check,no_root_squash)`

**And do this to export or unexport all directories** 

`exportfs -a`

**Start and enable server**

`systemctl enable --now nfs-kernel-server`

**Add a user for nfs**

`adduser vin --home /mnt/raid5_contas/vin`

**And your done with NFS server** ✔️



**For nis server now do this**

**Install it**

`apt -y install nis`

**Go to nano /etc/default/nis and change to this**

`NISSERVER=master`

`NISCLIENT=false`

**Go to nano /etc/ypserv.securenets and place your netmask and IP**

`#0.0.0.0 0.0.0.0`

`255.255.X.X 172.31.X.X`

**Go to /var/yp/Makefile and change from false to true**

`MERGE_PASSWD=true`

`MERGE_GROUP=true`

**Do your /etc/hosts**

`172.31.X.X central.inova.pt central inova.pt`

`172.31.X.X control.inova.pt control inova.pt`

**Update your database of nis with**

`/usr/lib/yp/ypinit -m`

**Go to cd /var/yp**

**And do** `make`

**And its done**
