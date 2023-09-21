---
title: Run CMAQ on the HPC7g Cluster
weight: 23
---

:::alert{type=info}
The CMAQ run script has been configured to run on 192 cores (3 compute nodes of hpc7g with 64 cores/node)
:::


1. **Change directories to the run script location**

```csh
cd /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts
```

2. **Verify the run script (`run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.csh`) is set to run for 1 day.

```csh
grep _DATE run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.csh
```

Output

```
set START_DATE = "2017-12-22"     #> beginning date (January 22, 2017)
set END_DATE   = "2017-12-22"     #> ending date     
```


2. **Load the Environment Modules**

```csh
module load gcc/gcc-9.3 ioapi-3.2/gcc-9.3-netcdf netcdf-4.8.1/gcc-9.3
```

3. **Submit the Run script to the SLURM queue**

```csh
sbatch run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.csh
```

4. **Check the status of the job**

```csh
squeue
```

Output

```
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
                 1   compute     CMAQ   ubuntu CF       0:30      3 compute-dy-hpc7g-[1-3]
```

Wait for the status to change from CF to R

5. If the job fails to run, then verify your username is ec2-user

```csh
whoami
```

If the output is ssm-user, then use the following command to switch users, and resubmit the job.

6. Switch to ec2-user

```csh
sudo su ec2-user
```

7. **Re-Submit the Run script to the SLURM queue**

```csh
sbatch run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.csh
```


8. **Login to the compute node**

```csh
ssh -Y compute-dy-hpc7g-1
```

5. **Run htop on the compute node**

```csh
htop
```

Output

![ec2-user](/static/images/2-run-cmaq-htop.png)

6. **HTOP should show that 64 processes are running and that 80.2G out of 124 G of memory is being used.**


