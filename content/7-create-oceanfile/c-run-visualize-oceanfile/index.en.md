---
title: Run Visualize Ocean File Jupyter Notebook
weight: 22
--- 

1. **Run Jupyter Notebook to visualize the DMS and CHLO variables that were added to the OCEANFILE**

```csh
cd dmschlo
jupyter notebook
```

2. **Double click on the CMAQ_DMS_ChlorA_Plot.ipynb notebook**



3. **Use the Shift Enter keys to run each cell within the Jupyter Notebook**

Output:


![Successful DMS Chlora Plot](/static/images/8-CMAQ_DMS_Chlora_plot.png)

:::alert{type=info}
Note, if the Jupyer Notebook Kernel dies then there may not be enough memory to create the visualization.
Verify that the head node is a c7g.2xlarge with 8 vcpus and 16 GiB of memory.
:::
