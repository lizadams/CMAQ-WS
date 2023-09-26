---
title: Set up the Input Data
weight: 23
---

:::alert{type=info}
Note, either the YAML file used to create the cluster created an automatic link from the S3 bucket to the /fsx file system.
Or, the YAML file created a lustre file system with no S3 bucket Imported or linked to it.
The following instructions help to prepare the input data prior to running CMAQ.
[AWS Guide on Preloading Files](https://docs.aws.amazon.com/fsx/latest/LustreGuide/preload-file-contents-hsm-dra.html)
:::


1. **Change directories to the lustre filesystem and list the files**

```csh
cd /fsx
ls *
```

Output:

```
index.html  readme.html

CMAQv5.4_2018_12LISTOS_Benchmark_3Day_Input:
12LISTOS_Training

CMAQv5.4_2018_12NE3_Benchmark_2Day_Input:
2018_12NE3

CMAQv5.4_2018_12US1_Benchmark_2Day_Input:
2018_12US1

```

If there is no output, then the yaml file did not import the S3 bucket. Skip Step 2 and go to step 3.

2. **Pre-load the files from the S3 bucket to the Lustre Filesystem**

Change directires out of the parallel FSx for Lustre filesystem to the shared EBS volume

```csh
cd /shared
```

Use nohup to get Amazon FSx to copy data from your Amazon S3 data repository when a file is first accessed.
CMAQ is sensitive to latencies, so it is best to preload contents of individual files or directories using the following command:

```csh
nohup find /fsx/ -type f -print0 | xargs -0 -n 1 sudo lfs hsm_restore &
```

3. **If the input data is not already there, then copy the data from the s3://cmas-cmaq/ bucket using the following command**

```csh
aws s3 --no-sign-request cp --recursive s3://cmas-cmaq/CMAQv5.4_2018_12US1_Benchmark_2Day_Input /fsx/CMAQv5.4_2018_12US1_Benchmark_2Day_Input
```

4. **Create a directory that specifies the full path that the run scripts are expecting.**

```csh
mkdir -p /fsx/data/CMAQ_Modeling_Platform_2018/
```

5. **Link the 2018_12US1 directoy**

```csh
cd /fsx/data/CMAQ_Modeling_Platform_2018/
ln -s /fsx/CMAQv5.4_2018_12US1_Benchmark_2Day_Input/2018_12US1/ .
```

6. **Create the output directory**

```csh
mkdir -p /fsx/data/output
```
