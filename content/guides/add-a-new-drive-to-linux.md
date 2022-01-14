---
title: "Adding a new drive to a linux machine"
date: 2022-01-12
draft: false
description: "In this guide, we'll add a new disk, and format it for use."
slug: "adding-a-new-drive-to-linux"
tags: ["guide"]
---

{{< lead >}}
In this guide, we'll add a new disk, and format it for use.
{{< /lead >}}

This guide makes assumptions about drive lettering and paths, ensure you're running things where you want to.

------

1. Determine drive name and logical size.
```
fdisk -l
```
![](/images/f6262d79-3f62-4db6-adc9-08f3c1e1513f.png)

2. Partition drive using fdisk
```
fdisk /dev/sdc
```
- Common commands
```
n – Create partition
p – print partition table
d – delete a partition
q – exit without saving the changes
w – write the changes and exit.
```

3. Create Partition using whole Block Device, defaults are fine

![](/images/4e337b43-3617-4f0d-9231-848273f628a9.png)

4. Determine partition name
```
lsblk
```

![](/images/4dc0e519-cec1-426f-956a-a135b2339196.png)

5. Make the file system
```
mkfs.xfs /dev/sdc1
```

6. Mount the drive, a few improvements related to random read in the form of noatime
```
mount -t xfs -o noatime,nodiratime /dev/sdc1 /mnt/block/rust/
```

7. Verify that the filesystem is mounted

8. To persists across reboots, ensure /etc/fstab updated with he following line.
```
/dev/sdc1 /mnt/block/rust/ xfs defaults,noatime,nodiratime 0 0
```


