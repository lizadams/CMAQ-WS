---
title: Get to know the CMAQ run script
weight: 23
---

Note, for all of these instructions click the copy content icon button on the top right of each panel and then use Control^V to paste the contents into the SSM Connnect Terminal or the DCV Terminal. 

Example image:

![click to copy contents](/static/images/2-click-to-copy-from-terminal.png)

Instructions:

1. **View the top of the run script.**

```csh
cd /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts/
head run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.csh
```

Output:

```
#!/bin/csh -f

## For Parallel Cluster 64 cores x 3 = 192 
## data on /fsx or lustre data directory
## https://dataverse.unc.edu/dataset.xhtml?persistentId=doi:10.15139/S3/LDTWKH
#SBATCH --nodes=3
#SBATCH --ntasks-per-node=64
#SBATCH --exclusive
#SBATCH -J CMAQ
#SBATCH -o /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts/run_cctm5.4+_Bench_2018_12US1_cb6r5_ae6_20200131_MYR.192.12x16pe.2day.20171222start.3x64.log
```

Note, this section of the run script determines how many compute nodes will be provisioned, and how many cores per node will be used.


2. **View the domain decomposition settings in the run script**

```csh
grep -B 2 NPCOL run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.csh
```

Output

```

#> Horizontal domain decomposition
if ( $PROC == serial ) then
   setenv NPCOL_NPROW "1 1"; set NPROCS   = 1 # single processor setting
else
   @ NPCOL  =  12; @ NPROW =  16
   @ NPROCS = $NPCOL * $NPROW
   setenv NPCOL_NPROW "$NPCOL $NPROW"; 

```

:::alert{type=info}
Note, that the multiplication of `NPCOL x NPROW` must equal the number of MPI ranks, which is defined in the Slurm settings `nodes * ntasks-per-node`.

Example.

```
NPCOL x NPROW
12    x 16    = 192

nodes x ntasks-per-node

3     x  64   = 192
```
:::

