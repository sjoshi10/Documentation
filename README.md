# Documentation


### How to setup VPN
https://openvpn.net/index.php/access-server/docs.html?id=229

### Create lvm

```
pvcreate /dev/sdb
vgcreate volume_group /dev/sdb
lvcreate -l 95%VG -n lvm_name volume_group
mkfs.ext4 /dev/mapper/volume_group-lvm_name
mount /dev/mapper/volume_group-lvm_name /mnt
```
