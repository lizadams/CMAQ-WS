---
title: Run CMAQ on HPC cluster
weight: 20
--- 

### CMAQ

:::alert{type=info}
Additional resources for the CMAQ: The Community Multiscale Air Quality Modeling System

https://www.epa.gov/cmaq

https://cmascenter.org/
:::


The Community Multiscale Air Quality (CMAQ) modeling system an active open-source development project of the U.S. EPA. The CMAQ system is a Linux-based suite of models that requires significant computational resources and specific system configurations to run. CMAQ combines current knowledge in atmospheric science and air quality modeling, multi-processor computing techniques, and an open-source framework to deliver fast, technically sound estimates of ozone, particulates, toxics and acid deposition. 


* Review the run script
* Review the input data
* Preload the input data on the lustre file system /fsx
* Submit the run script to the SLURM queue
* Use HTOP to examine the performance
* Review the timings after the run has completed
* Visualize CMAQ output
