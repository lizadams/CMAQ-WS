---
title: Review timings for CMAQ on the HPC7g Cluster
weight: 23
---


1. **Change directories to the run script location**

```csh
cd /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts
```


2. **Use tail to review the timing**

```csh
tail -n 20 run_cctm5.4+_Bench_2018_12US1_cb6r5_ae6_20200131_MYR.192.12x16pe.2day.20171222start.3x64.log
```

Output

```
tail -n 20 run_cctm5.4+_Bench_2018_12US1_cb6r5_ae6_20200131_MYR.192.12x16pe.1day.20171222start.3x64.log

\\\\\=====\\\\\=====\\\\\=====\\\\\=====/////=====/////=====/////=====/////


==================================
  ***** CMAQ TIMING REPORT *****
==================================
Start Day: 2017-12-22
End Day:   2017-12-22
Number of Simulation Days: 1
Domain Name:               12US1
Number of Grid Cells:      4803435  (ROW x COL x LAY)
Number of Layers:          35
Number of Processes:       192
   All times are in seconds.

Num  Day        Wall Time
01   2017-12-22   1593.6
     Total Time = 1593.60
      Avg. Time = 1593.60

```


3. **Compare the timing with the results in the [CMAQ on AWS Tutorial](https://pcluster-cmaq.readthedocs.io/en/latest/user_guide_pcluster/Performance-Opt/performance-optimization.html#benchmark-timing-for-hpc7g-16xlarge-with-64-processors-per-node)**

Note, the timings reported on the Tutorial are for 2 days, rather than 1 day
