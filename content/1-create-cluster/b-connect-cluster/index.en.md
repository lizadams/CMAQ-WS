---
title: Connect to the cluster
weight: 22
--- 

#### Option 1: SSM Connect (for running jobs)

1. After cluster creation completes, with the created cluster selected, choose **Shell** to access the cluster head node.

    ![Connect cluster - shell](/static/images/1-connectcluster-shell.png)

2. Verify you are logged in as ec2-user

```csh
whoami
```

Your user should be similar to ec2-user@ip-<IP-address>. If it is otherwise something like sh-4.2 or ssm-user@<IP-address>, then run the following command before proceeding:

```csh
sudo su ec2-user
```

3. Switch to .tcsh shell 

```csh
cp /shared/pcluster-cmaq/install/tcshrc.pcluster-spack-conda ~/.tcshrc 
```

4. Change to .tcsh shell

```csh
/bin/tcsh
``` 

5. Verify that the environment modules have  been loaded

```csh
module list
```



#### Option 2: DCV - for activities where you need to use X11 imagemagick display (creating plots)

1. After cluster creation completes, with the created cluster selected, choose **DCV** to access the cluster head node.

    ![Connect cluster - DCV](/static/images/1-connectcluster-dcv.png)

2. A new tab will pop up.

* Your browser may prompt you about the pop-up. Please allow pop-ups from the AWS ParallelCluster UI domain. 

* DCV uses self-signed certificates, and your browser may warn you about a potentials security risk. You will need to click on **Advanced**, and then **Accept the Risk and Continue**. 

    ![Connect cluster - DCV pop-up](/static/images/1-connectcluster-dcvpopup.png)

3. To launch a terminal (where the rest of the workshop will run), click **Activities**, then **Applications Grid**, then **Terminal**. 

    ![Connect cluster - DCV terminal](/static/images/6-verdi-dcv-select-terminal.png)
