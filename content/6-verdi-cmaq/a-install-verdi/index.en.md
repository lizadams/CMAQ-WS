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

3. **Install Java 17 and VERDI.**

```csh
sudo yum install -y java-17-amazon-corretto
pip install gdown
gdown 'https://drive.google.com/uc?export=download&id=1Hrr_0N09RN4g8g8lZ4bFQZWR3nABade_'
tar xf VERDI_2.1.4_linux64_20221007.tar.gz
cd VERDI_2.1.2
sed -i 's/^JAVA=.*/JAVA=$(which java)/' verdi.sh
```

