---
title: Visualize Results using Jupyter Notebook
weight: 20
--- 

:::alert{type=info}
   The CMAQ output files from the Base and DESID Emission Reduction CMAQ runs were pre-saved to the /shared/build/openmpi-gcc/CMAQv5.4+/data/output directory.
This will allow you to try out the Jupyter Notebook and the VERDI visualizations without needing to complete the CMAQ runs that output to the /fsx/data/output directory.
:::

**For this training, use DCV.**

:::alert{type=info}
Note: it might be easier to use tab completion, start entering a directory or file name and then use the tab key, as you have to sync your local copy-cut-paste buffer with the remote buffer when using DCV.
![Sync buffers](/static/images/dcv-sync.png)
:::

NICE DCV is a high-performance remote display protocol that provides customers with a secure way to deliver remote desktops and application streaming from any cloud or data center to any device, over varying network conditions. Connect to the [cluster using DCV](http://localhost:8080/en-US/1-create-cluster/b-connect-cluster#option-2:-dcv-only-for-jupyter-notebook-and-verdi-applications-that-require-x11-imagemagick-display-(creating-plots)).

There are additional methods to create plots of CMAQ Output Data, and some of this is being shared as scripts.
Typically these files end in an extention that reflects their contents as follows:
R (.R), Python (.py), and Jupyter Notebook (.ipynb)

**Spatial Plots of Daily Average Difference**

This plot was developed by Sara Farrell from US EPA.
   
1. **Main_Purpose**

This script works to create spatial difference plots for each variable in the two CMAQ output files
   
2. **Other_Features**

a. Works with <font color="teal">**Lambert Conformal**</font> (CONUS and states/localities within) and <font color="purple">**Stereographically**</font> (N. Hemispheric) Projected output<br>

:::alert{type=info}
   If you need another spatial domain not covered Sara Farrell can add one in!
:::

b.  Showcases colorgrid options

c.  Extracts time, projection, species and units from file headers
 
3. **General Instructions**

a) You run each cell by clicking in it and then pressing Enter+Shift

b) You will be prompted to provide some inputs such as color schemes, and time zone information, etc

:::alert{type=info}
If you have any feedback or need help, please submit an issue in the Python Category on the CMAS Center Forum https://forum.cmascenter.org/c/python/58 and mention Sara using `@slfarrell` in the issue to obtain her help.
:::

