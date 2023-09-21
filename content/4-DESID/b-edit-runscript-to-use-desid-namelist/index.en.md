---
title: Edit the CMAQ Run script (optional)
weight: 23
---

1. **Copy the Run script and edit it to use the DESID namelist files**

```csh
cd /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts/BLD_CCTM_v54+_gcc
cp run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.csh run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic_DESID_RED_NY.csh
```

2. **Change APPL to a new name**

'''csh
set APPL      = 12US1_DESID_REDUCE        #> Application Name (e.g. Gridname)
```

3. **verify the following emission stream names match the names used in the DESID namelist.**

```csh
grep STK_EMIS_LAB_00 ../run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.DESID_RED_NY.csh 
```

Output

```
setenv STK_EMIS_LAB_001 PT_NONEGU
  setenv STK_EMIS_LAB_002 PT_EGU
  setenv STK_EMIS_LAB_003 PT_OTHER
  setenv STK_EMIS_LAB_004 PT_AGFIRES
  setenv STK_EMIS_LAB_005 PT_FIRES
  setenv STK_EMIS_LAB_006 PT_RXFIRES
  setenv STK_EMIS_LAB_007 PT_OTHFIRES
  setenv STK_EMIS_LAB_008 PT_OILGAS
  setenv STK_EMIS_LAB_009 PT_CMV_C1C2
```

4. **Compare the above settings to those used in the Emission Stream Family defined in the DESID Namelist.**

```csh
grep -A 2 -B 2 StreamFamilyMembers CMAQ_Control_DESID_RED_EGU_POINT_NY.nml
```


Output

```
  StreamFamilyName(1)     = 'PT_SOURCES'
  StreamFamilyMembers(1,1:4)= 'PT_NONEGU','PT_OTHER', 'PT_AGFIRES', 'PT_FIRES', 'PT_RXFIRES', 'PT_OTHFIRES', 'PT_OILGAS','PT_CMV_C1C2'

  StreamFamilyName(2)     = 'PT_EGUS'
  StreamFamilyMembers(2,1:1)= 'PT_EGU'
```

:::alert{type=info}
CMAQ won’t crash if the stream name in CMAQ_Control_DESID_<MECH>_RED_EGU_POINT_NY.nml was set incorrectly. CMAQ just ignores the incorrect stream name and won’t apply scaling.
:::

5. **update the DESID namelist file names in the run script to use the Reduced PT_EGU and diagnostic instructions.**

```csh
cd  /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts/BLD_CCTM_v54+_gcc
gedit run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic_DESID_RED_NY.csh
```

Modify the namelist setting to use the DESID namelist:

```csh
setenv DESID_CTRL_NML ${BLD}/CMAQ_Control_DESID_RED_EGU_POINT_NY.nml
setenv DESID_CHEM_CTRL_NML ${BLD}/CMAQ_Control_DESID_${MECH}_RED_EGU_POINT_NY.nml
```

6. **update the Spatial Masks for Emissions Scaling to use a file that contains state definitions for New York.**

```csh
#> Spatial Masks For Emissions Scaling
  setenv CMAQ_MASKS $SZpath/GRIDMASK_STATES_12US1_m3clple_12listos.ncf
```

7. **verify that the file contains New York**

```csh
ncdump /shared/build/GRIDMASK/GRIDMASK_STATES_12US1.nc | grep NY
```

Output

```csh
	float NY(TSTEP, LAY, ROW, COL) ;
		NY:long_name = "NY              " ;
		NY:units = "fraction        " ;
		NY:var_desc = "NY fractional area per grid cell   
```
