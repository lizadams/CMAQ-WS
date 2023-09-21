---
title: Run CMAQ using DESID to reduce emissions on the HPC7g Cluster
weight: 23
---

:::alert{type=info}
The CMAQ run script has been configured to run on 192 cores (3 compute nodes of hpc7g with 64 cores/node)
:::


1. **Change directories to the run script location**

```csh
cd /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts
```

2. **Submit the Run script to the SLURM queue**
```csh
sbatch run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.DESID_RED_NY.csh
```

3. **Check the status of the job**

```csh
squeue
```

Output

```
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
                 1   compute     CMAQ   ubuntu CF       0:30      3 compute-dy-hpc7g-[1-3]
```

Wait for the status to change from CF to R

4. **Login to the compute node and run htop**

```csh
ssh -Y compute-dy-hpc7g-1
htop
```

![ec2-user](/static/images/2-run-cmaq-htop.png)

5. HTOP should show that 64 processes are running and that 80.2G out of 124 G of memory is being used.
