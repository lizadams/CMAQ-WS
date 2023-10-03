---
title: Create an HPC cluster
weight: 20
--- 

:::alert{type=info}
Note, the YAML file used to create the cluster uses a snapshot that was created using the Alinux2 Operating System
If you would like to install CMAQ on the Ubuntu 22.04.2 LTS OS, please follow instructions in the [developer guide](https://pcluster-cmaq.readthedocs.io/en/latest/user_guide_pcluster/developers_guide/cmaq-vm/install_64-bit-arm.html) to install the CMAQ libraries and code.
:::

### AWS ParallelCluster 

AWS ParallelCluster is an AWS-supported, open source cluster management tool that makes it easy for you to deploy and manage High Performance Computing (HPC) clusters on AWS. ParallelCluster uses a simple (YAML) text file to model and provision all the resources needed for your HPC applications in an automated and secure manner. 

We’re going to use the AWS ParallelCluster UI, which we installed in the the previous section, to create a cluster.

We’ve broken the steps down to:

* Create a Cluster with AWS ParallelCluster
* Connect to the cluster
* Get to know the cluster
* Load Environment Modules 
* Run CMAQ
* Visualize CMAQ output
