+++
categories = ["guide"]
date = 2022-01-12T13:00:00Z
description = ""
featured = ""
featuredalt = ""
featuredpath = ""
linktitle = ""
slug = "create-swap-on-centos"
title = "Create swap on CentOS"
type = "guide"

+++
This guide will provide steps on the quickest way to create a swap file on CentOS, should work on both CentOS 7, 8 and Stream. Before proceeding with this tutorial, check if your CentOS installation already has swap enabled by typing:

```
sudo swapon --show
```

1. Create file

```  
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```

2. Lock to root perms

```
sudo chmod 600 /swapfile
```

3. Make Swap and enable it

```
sudo mkswap /swapfile
sudo swapon /swapfile
```

4. Persist on boot

```
sudo vi /etc/fstab
```

```
/swapfile swap swap defaults 0 0
```

5. Change swappiness

```
vi /etc/sysctl.conf 
vm.swappiness=10
```