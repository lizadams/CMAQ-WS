---
title: Visualize Results using Jupyter Notebook
weight: 20
--- 

For this training, use the DCV.

NICE DCV is a high-performance remote display protocol that provides customers with a secure way to deliver remote desktops and application streaming from any cloud or data center to any device, over varying network conditions.

There are additional methods to create plots of CMAQ Output Data, and some of this is being shared as scripts.
Typically these files end in an extention that reflects their contents as follows:
R (.R), Python (.py), and Jupyter Notebook (.ipynb)

**Spatial Plots of Daily Average Difference**

This plot was developed by Sara Farrell from US EPA.
   
1. **Main_Purpose**

This script works to create spatial difference plots for each variable in the two CMAQ output files
   
2. **Other_Features**

a. Works with <font color="teal">**Lambert Conformal**</font> (CONUS and states/localities within) and <font color="purple">**Stereographically**</font> (N. Hemispheric) Projected output

If you need another spatial domain not covered Sara Farrell can add one in!
b.  Showcases colorgrid options
c.  Extracts time, projection, species and units from file headers
 
3. **General Instructions**

a) You run each cell by clicking in it and then pressing Enter+Shift
b) You will be prompted to provide some inputs such as color schemes, and time zone information, etc
c) This is in it's beta form so if you have any feedback or need help, please submit an issue on CMAS Center Forum https://forum.cmascenter.org/c/python/58 and mention Sarah using `@slfarrell` in the issue to obtain her help.

