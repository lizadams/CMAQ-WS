---
title: Connect to the cluster with DCV
weight: 23
---

1. **Follow the instructions to [connect with DCV](/1-create-cluster/b-connect-cluster#option-2:dcv) and launch a terminal.**

![MATE Terminal](/static/images/6-verdi-dcv-select-terminal.png)


2. **Install Imagemagick and Firefox**

Note: if you do not have cut-and-paste working in the Nice DCV, you can use the SSM Connect - Shell to do the following  installation.

```csh
sudo yum makecache fast
sudo yum install -y ImageMagick ImageMagick-devel
sudo yum install amazon-linux-extras firefox -y
```

Verify ImageMagick is installed and working, launch it on the Nice DCV.

```csh
display
```

Output

![ImageMagick Display](/static/images/1-imagemagick-display.png)

