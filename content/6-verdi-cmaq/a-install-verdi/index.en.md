---
title: "Install VERDI on HPC cluster"
weight: 20
---

1. **Follow the instructions to [connect with DCV](/1-create-cluster/b-connect-cluster#option-2:dcv) and launch a terminal.**

![MATE Terminal](/static/images/6-verdi-dcv-select-terminal.png)

2. **Switch to tcsh shell.**

```csh
/bin/tcsh
```

3. **Install Java 17**

```csh
sudo yum install -y java-17-amazon-corretto
```

