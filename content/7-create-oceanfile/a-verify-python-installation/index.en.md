---
title: Verify the Python Installation for PYTOOLS
weight: 21
--- 

1. **Follow the instructions to [connect with DCV](/1-create-cluster/b-connect-cluster#option-2:dcv) and launch a terminal.**

![MATE Terminal](/static/images/6-verdi-dcv-select-terminal.png)

2. **Change directories to the PYTOOLS location**

```csh
cd /shared/build/CMAQ_REPO_v54+/PYTOOLS/
```

3. **Verify the libraries are available on the Python Installation**

```csh
python install/show_versions.py install/requirements.txt
```



