---
title: CMAQ Benchmark Data on S3 Bucket
weight: 23
---

The CMAS Data Warehouse within the Registry of Open Data on AWS contains several S3 buckets that are open to public use.

The CMAQ Benchmark Data used for this training comes from the following S3 bucket.

[CMAS Data Warehouse on AWS](https://registry.opendata.aws/cmas-data-warehouse/)

Screenshot image of bucket on AWS:

   ![s3:cmas-cmaq](/static/images/2-cmaq-benchmark-data-s3.png)

Instructions:

1. **Click on [Browse Bucket](https://cmas-cmaq.s3.amazonaws.com/index.html) to explore the data on the S3 bucket**

Note, this data is uncompressed and saved in a directory structure that matches the CMAQ Benchmark scripts.

2. **Review the top section of the readme.html**

[readme.html](https://cmas-cmaq.s3.amazonaws.com/readme.html)

Output (top 6 lines)

```
Downloading data from S3 Bucket
This dataset is available as part of the AWS Open Data Program, therefore egress fees are not charged to either the host or the person downloading the data.
Instructions for downloading the aws command line.

Instructions to Download AWS Command Line
Once you have it installed, you can use it without credentials.

```


3. **Query how much data is in the 12US1 benchmark case**

```csh
aws s3 ls --summarize --human-readable --recursive s3://cmas-cmaq/CMAQv5.4_2018_12US1_Benchmark_2Day_Input
```

Output:

```
Total Objects: 247
   Total Size: 84.9 GiB

```

4. **Command to copy data to local filesystem** (optional)

Command to copy files from the bucket to your local filesystem (the system where you are running the aws cli) and place it under the path that you specify for /your_local_path.

```csh
aws s3 --no-sign-request cp --recursive s3://cmas-cmaq/CMAQv5.4_2018_12US1_Benchmark_2Day_Input /your_local_path/
```

Output (demonstrating the high transfer rate of 27Mib/sec)

![aws copy rate](/static/images/2-aws-cp-transfer-rate.png)


:::alert{type=info}
For this training, the data will be pre-loaded from the S3 bucket to the /fsx or Lustre File System
:::

