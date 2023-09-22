---
title: CMAQ Data on AWS 
weight: 23
---

[CMAS Data Warehouse](https://registry.opendata.aws/cmas-data-warehouse/) 

**Description of Data currently available:**


| S3 Bucket                     | ncdump -k | Storage method | Extension | Size |
| ---------------------------------------------------------------------------------------------------------------------------------  | --------------------  |  ------                    | ------ | --------  |
| **CMAQ Input Data**                                                                                                                |                       |                            |        |           |
| [CMAQ Release Benchmark Data for Easy Download](https://cmaq-release-benchmark-data-for-easy-download.s3.amazonaws.com/index.html) | tar.gz                | archive                    | tar.gz | 24.2 GiB  |
| [CMAQ CONUS-2 Benchmark Data](https://cmas-cmaq-conus2-benchmark.s3.amazonaws.com/index.html)                                      | netcdf-3 classic      | intact directory structure | .ncf   | 461.8 GiB |
| [CMAQ Benchmark Data](https://cmas-cmaq.s3.amazonaws.com/index.html)                                                               | netcdf-3 classic      | intact directory structure | .nc    | 142.1 GiB |
| [CMAS WWLLN Lightning Data](https://cmas-wwlln-lightning.s3.amazonaws.com/index.html)                                              | netcdf-3 classic      | intact directory structure | .ioapi | 31.4 GiB  |
| [EQUATES EPA’s Air QUAlity TimE Series Project Data](https://cmas-equates.s3.amazonaws.com/index.html)                             | netcdf-4 compressed   | intact directory structure | .ncf   | 4.3 TiB   |
| [CMAQ 2018 Modeling Platform](https://cmas-cmaq-modeling-platform-2018.s3.amazonaws.com/index.html)                                | netcdf-4 compressed   | intact directory structure | .nc4   | 6.1 TiB   |
|                                                                                                                                    |                       |                            |        |           |
| **AMET Observational Input Data**                                                                                                  |                       |                            |        |           |
| [AMET Data](https://cmas-amet.s3.amazonaws.com/index.html)                                                                         | netcdf-3 classic      | intact directory structure | .nc    | 834.6 GiB | 
|                                                                                                                                    |                       |                            |        |           |
|**SMOKE Emissions Platforms Data**                                                                                                  |                       |                            |        |           |
| [2019 Modeling Platform](https://2019platform.s3.amazonaws.com/index.html)                                                         | netcdf-3 classic      | intact directory structure | ncf.gz | 2.0 TiB   |
| [2016v3 Modeling Platform](https://2016v3platform.s3.amazonaws.com/index.html)                                                     | netcdf-3 classic      | mix                 | .camx/.ncf/zip  | 35.2 TiB  |
| [SMOKE 2016 Modeling Platform](https://cmas-smoke-modeling-platform-2016.s3.amazonaws.com/index.html)                              | netcdf-3 classic      | mix                 |   .ncf/zip      | 392.6 GiB |

:::alert{type=info}
For this training, the data will be pre-loaded from the S3 bucket to the /fsx or Lustre File System from the CMAQ Benchmark Data S3 Bucket.
To run CMAQ, the CMAQ run script specifies the directory location matching that on the S3 bucket and using a module environment that supports the netCDF file type.
:::

