---
title: "Install VERDI on HPC cluster"
weight: 20
---

### Login to cluster using the Nice DCV 

### Select Activities > Show Applications > Select MATE Terminal

1. Select Terminal within the DCV

   ![DCV terminal](/static/images/6-verdi-dcv-select-terminal.png)

2. Switch to tcsh shell

```csh
/bin/tcsh
```

3. Verify that VERDI is installed

```csh
which verdi.sh
```

4. Verify headless display is available

```csh
ls -rlt /usr/lib/jvm/java-17-amazon-corretto.aarch64/lib/libawt.so
```

5. If needed, install library for headless display ( to use copy/paste function, install this on the SSM Connect terminal

```csh
wget https://download.oracle.com/java/17/archive/jdk-17.0.8_linux-aarch64_bin.rpm
sudo rpm -ivh jdk-17.0.8_linux-aarch64_bin.rpm
```

