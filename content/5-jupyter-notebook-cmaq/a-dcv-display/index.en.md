---
title: Connect to the cluster with DCV
weight: 23
---

1. **Follow the instructions to [connect with DCV](/1-create-cluster/b-connect-cluster#option-2:dcv) and launch a terminal.**

![MATE Terminal](/static/images/6-verdi-dcv-select-terminal.png)

1. **Install Imagemagick and Firefox**

```csh
sudo bash
yum update
yum makecache fast
yum install -y ImageMagick ImageMagick-devel
amazon-linux-extras install -y firefox
exit
```

Verify ImageMagick is installed and working, launch it.
```csh
display
```

Output

![ImageMagick Display](/static/images/1-imagemagick-display.png)

