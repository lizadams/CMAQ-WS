---
title: Edit DESID Namelists to Reduce Point Source EGU Emissions by 25%  (optional)
weight: 23
---

Note - these were the steps that were taken to set up CMAQ to run using the DESID Chemical Species Control file.
Please review - do not re-edit the files.

1. **Edit the CMAQ DESID Chemical Species Control File**

```csh
cd /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts/BLD_CCTM_v54+_gcc
cp CMAQ_Control_DESID_cb6r5_ae7_aq.nml CMAQ_Control_DESID_cb6r5_ae7_aq_RED_EGU_POINT_NY.nml
vi CMAQ_Control_DESID_cb6r5_ae7_aq_RED_EGU_POINT_NY.nml
```

2. **Add the following lines to the bottom of the file according to the DESID Tutorial Instructions** 

https://github.com/USEPA/CMAQ/blob/main/DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_emissions.md#scale_stream
(place the line before the / file marker)

```csh
   ! PT_EGU Emissions Scaling reduce PT_EGU emissions in New York by 25%. Note, to reduce the emissions by 25% we use DESID to multiply what had been 100% emissions by .75, so that the resulting emissions is reduced by 25%.
   'NY'  , 'PT_EGU'      ,'All'    ,'All'         ,'All' ,.75    ,'UNIT','o',
```

3. **Activate DESID Diagnostics**

Create a DESID Control File and edit it to define NY as a region, and activate DESID emissions diagnostics
Define NY as a region in the DESID Region Definitions

```csh
cp CMAQ_Control_DESID.nml CMAQ_Control_DESID_RED_EGU_POINT_NY.nml
gedit  CMAQ_Control_DESID_RED_EGU_POINT_NY.nml &
```

Modify the following section to use the NY region that is specified in the CMAQ_MASKS file, note the CMAQ_MASKS file is defined in the DESID Run script.

```csh
&Desid_RegionDef
 Desid_Reg_nml  =
 !            Region Label   | File_Label  | Variable on File
 !              'EVERYWHERE'  ,'N/A'        ,'N/A',
               'NY'         ,'CMAQ_MASKS' ,'NY',
 !<Example>    'ALL'         ,'ISAM_REGIONS','ALL',
/
```

4. **Create two stream family definitions, one that includes all point source emissions, and the second that only contains PT_EGU**

```csh
!------------------------------------------------------------------------------!
! Emissions Scaling Family Definitions                                         !
!    This component includes definitions for families of emission streams and  !
!    region combinations.                                                      !
!------------------------------------------------------------------------------!
&Desid_StreamFamVars
 Desid_N_Stream_Fams = 2           ! Exact number of stream family definitions
 Desid_Max_Stream_Fam_Members = 20 ! Larger than the number of streams on all
                                   ! family definitions
/

&Desid_StreamFam
! For emission streams available in several run scripts under CCTM/scripts

  StreamFamilyName(1)     = 'PT_SOURCES'
  StreamFamilyMembers(1,1:8)= 'PT_NONEGU','PT_OTHER', 'PT_AGFIRES', 'PT_FIRES', 'PT_RXFIRES', 'PT_OTHFIRES', 'PT_OILGAS','PT_CMV_C1C2'

  StreamFamilyName(2)     = 'PT_EGUS'
  StreamFamilyMembers(2,1:1)= 'PT_EGU'
&Desid_Diag
```

5. **activate DESID diagnostics to report the reduction in PT_EGU emissions.**

Note, if you define only one diagnostic rule, you must comment out all other rules.

```csh
&Desid_DiagVars
  Desid_N_Diag_Rules = 1    ! Exact Number of Diagnostic Rules Below
  Desid_Max_Diag_Streams=20 ! Maximum number of species variables on all rules
                            ! below (do not count expansions)
  Desid_Max_Diag_Spec = 80  ! Maximum number of species variables on all rules
                            ! below (do not count expansions)
/
```

```csh
! Create a diagnostic of the sum of the components of the PT_SOURCES
 ! family (defined in the stream family section). This file will be column sums
 ! and will include all the emitted species as long as they appear on at least
 ! one of the streams within PT_SOURCES.

 

    Desid_Diag_Streams_Nml(1,:)= 'PT_EGUS'
    Desid_Diag_Fmt_Nml(1)      = 'COLSUM'
    Desid_Diag_Spec_Nml(1,:)   = 'ALL'
```

6. **Verify that the settings are correct by comparing to the version in the github repo directory**

```csh
diff CMAQ_Control_DESID_RED_EGU_POINT_NY.nml /shared/pcluster-cmaq/qa_scripts/workshop/CMAQ_Control_DESID_RED_EGU_POINT_NY.nml
```

3. **Copy the Run script and edit it to use the DESID namelist files**

```csh
cd /shared/build/openmpi_gcc/CMAQ_v54+/CCTM/scripts/BLD_CCTM_v54+_gcc
cp run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic.csh run_cctm_2018_12US1_v54_cb6r5_ae6.20171222.3x64.ncclassic_DESID_RED_NY.csh
```


:::

