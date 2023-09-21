---
title: "Install VERDI on HPC cluster"
weight: 20
---

### Login to cluster using the Nice DCV 

### Select Activities > Show Applications > Select MATE Terminal

1. Select Terminal within the DCV

   ![DCV terminal](/static/images/6-verdi-dcv-select-terminal.png)


### Verify that VERDI is installed

```csh
which verdi.sh
```

### Verify headless display is available

```csh
ls /usr/lib/jvm/java-17-amazon-corretto.aarch64/lib
```

### If needed, install library for headless display

```csh
wget https://download.oracle.com/java/17/archive/jdk-17.0.8_linux-aarch64_bin.rpm
sudo rpm -ivh jdk-17.0.8_linux-aarch64_bin.rpm
```

