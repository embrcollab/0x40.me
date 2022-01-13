+++
categories = ["guide"]
date = 2022-01-14T13:00:00Z
description = "Extending an LVM partition with GParted"
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
slug = "direct-play-for-plex"
title = "Direct Play for Plex"
type = ""

+++

## Extending an LVM partition with GParted

Follow guide at own risk, resizing disks comes with risk, make sure you have backups. This guide assumes paths, make sure you're running commands agains the correct drives/paths.

1. Grow disk in Hypervisor
2. Use Gparted to increase logical volume size
3. Run `vgdisplay` - find the "VG Name", in my sitation it's d0
4. Extend the LVM volume
```
lvextend -l +100%FREE /dev/d0/root
```

5. expand the file system, either using resize2fs or xfx_growfs if using centOS and XFS
This
```
xfs_growfs /dev/d0/root
```
Or this depending on FS type
```
resize2fs /dev/d0/root
```

6. verify change has gone through  
```
df -h
```

---

## Extending an LVM partition with fdisk and without a reboot.

You can do this without rebooting in CentOS 7. Assuming your disk is /dev/vda and standard RHEL/CentOS partitioning:  
Extend partition  

```
# fdisk /dev/vda
```

Enter `p` to print your initial partition table.  
Enter `d` (delete) followed by `2` to delete the existing partition definition (partition 1 is usually /boot and partition 2 is usually the root partition).  
Enter `n` (new) followed by `p` (primary) followed by `2` to re-create partition number 2 and `enter` to accept the start block and `enter` again to accept the end block which is defaulted to the end of the disk.  
Enter `t` (type) then `2` then `8e` to change the new partition type to "Linux LVM".  
Enter `p` to print your new partition table and make sure the start block matches what was in the initial partition table printed above.  
Enter `w` to write the partition table to disk. You will see an error about `Device or resource busy` which you can ignore.  
Update kernel in-memory partition table  
After changing your partition table, run the following command to update the kernel in-memory partition table:  

```
# partx -u /dev/vda
```
Resize physical volume  
Resize the PV to recognize the extra space  

```
# pvresize /dev/vda2
```

Resize LV and filesystem  
In this command `centos` is the PV, `root` is the LV and `/dev/vda2` is the partition that was extended. Use `pvs` and `lvs` commands to see your physical and logical volume names if you don't know them. The `-r` option in this command resizes the filesystem appropriately so you don't have to call `resize2fs` or `xfs_growfs` separately.  

```
# lvextend -r centos/root /dev/vda2
```