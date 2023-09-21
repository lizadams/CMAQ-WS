---
title: "Use VERDI to visualize the change in Ozone and PM2.5 due to reducing emissions from PT_EGU sources in New York"
weight: 20
--- 

### Run VERDI to look the change in Ozone

Note, it is difficult to copy and paste content to the NICE DCV.

Please use the following scripted versions.

```csh
cd /shared/pcluster-cmaq/qa_scripts/workshop
```

### Run VERDI to look at the change in PM2.5

```csh
./verdi_compare_NO2_CONC_DESID_vs_base.csh
```

### Zoom in to the State of New York

Use your mouse to click and then drag to the right to create a region or use the 

Controls > Set Row and Columns Ranges

Rows: 122, 236
Columns: 319, 402

Select 

Plot > Animate Plot

Then select Start on the Animate Plot window.

Where would you expect to see differences in concentrations between the base case and the DESID case?

Remember that the DESID run reduced PT_EGU emissions within NY by 25%, so we would only expect to see emissions changes due to that.
The extent of the impact will go beyond NY State, depending on the wind direction and wind speed that day.
