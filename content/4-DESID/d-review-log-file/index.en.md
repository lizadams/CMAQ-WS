---
title: Review CTM_LOG file for definition of Regions Available for Scaling and Emission Stream Family Definitions
weight: 23
---

:::alert{type=info}
The CMAQ run script has been configured to run on 192 cores (3 compute nodes of hpc7g with 64 cores/node)
:::


1. **Review the Emissions Scaling Report Section in the CTM_LOG File to verify that for the NY region, the EGU emissions were scaled by 75%**

```csh
cd output_v54+_cb6r5_ae7_aq_WR413_MYR_gcc_2018_12US1_3x64_classic_DESID_REDUCE
grep -A 20 'Stream Type: "Point Emissions File   2' CTM_LOG_001*
```

Output:

```csh
     Stream Type: "Point Emissions File   2" | Sector Label: PT_EGU (04)

        Table of Aerosol Size Distributions Available for Use Sector-Wide.
        Note that Mode 1 is reserved for gas-phase species and emission variable.
          Number  Em. Var.  Mode  Reference Mode (see AERO_DATA.F)
          ------  --------------  --------------------------------
          2       FINE                        FINE_REF
          3       COARSE                    COARSE_REF

        CMAQ Species     Phase/Mode  Em. Var.          Region             Op ScaleFac Basis FinalFac
        ------------     ----------  ---------         ------             -- -------- ----- --------
          NO2              GAS        NO2              EVERYWHERE         a   1.000    UNIT   1.000
                                                       NY                 o   0.750    UNIT   0.750
          NO               GAS        NO               EVERYWHERE         a   1.000    UNIT   1.000
                                                       NY                 o   0.750    UNIT   0.750
          HONO             GAS        HONO             EVERYWHERE         a   1.000    UNIT   1.000
                                                       NY                 o   0.750    UNIT   0.750
          SO2              GAS        SO2              EVERYWHERE         a   1.000    UNIT   1.000
                                                       NY                 o   0.750    UNIT   0.750
          SULF             GAS        SULF             EVERYWHERE         a   0.000    UNIT   0.000
                                                       NY                 o   0.750    UNIT   0.750
```

