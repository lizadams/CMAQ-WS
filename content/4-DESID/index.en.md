---
title: Run CMAQ using DESID to reduce PT_EGU emissions by 25% (optional)
weight: 20
--- 

### DESID

:::alert{type=info}
The Visualization using VERDI and Jupyter Notebook do not require this lab, as the output files from this lab were pre-generated and saved. Please review the instructions for how to modify CMAQ to run DESID.
:::


During this DESID exercise, you will:

* Review the DESID Documentation in Appendix B of the CMAQ User Manual: https://github.com/USEPA/CMAQ/blob/main/DOCS/Users_Guide/Appendix/CMAQ_UG_appendixB_emissions_control.md#appendix-b-emissions-input-and-control
* Review the DESID Tutorial: https://github.com/USEPA/CMAQ/blob/main/DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_emissions.md
* Edit CMAQ DESID Control Files: CMAQ_Control_DESID.nml and CMAQ_Control_DESID_cb6r5_ae7_aq.nml to specify a region and to multiply an emissions factor to the EGU sources by a factor of .75 to approximate shutting down coal fired power plants in New York and transitioning to renewable sources.
* Activate Region-Based Scaling to only reduce emissions from EGU plants from New York State.
* Activate DESID Diagnostics to verify that the Emissions from PT_EGU sources within New York State were reduced by 25%.
* Execute a new CCTM simulation that uses modified DESID Control Files to reduce emissions.
* Execute a second CCTM simulation that uses modified DESID Control Files that does not reduce emissions
* Examine the DESID emission diagnostic files for to verify that emissions were scaled by 25%
* Plot a comparison of output with and without DESID emission scaling to see the impact of reduced EGU emissions in New York on Ozone Concentration.
