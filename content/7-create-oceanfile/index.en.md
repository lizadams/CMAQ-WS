---
title: Python Tools for CMAQ (optional)
weight: 20
--- 

:::alert{type=info}
Additional instructions are available here:
https://github.com/USEPA/CMAQ/tree/main/PYTOOLS
:::

### Python Tools for CMAQ

Update an OCEAN File to add DMS and CHLO variables (optional)

If you have ocean in your domain, and you would like to use cb6r5 mechanism, then you need these additional variables added to the OCEANFILE for your domain.

For the full tutorial on how to create an OCEANFILE for cb6r5, please see https://github.com/USEPA/CMAQ/blob/main/DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_oceanfile.md

* Change directory to location of Python Tools
* Verify the Ocean File location
* Start the Jupyter Notebook
* Verify the prerequisite libraries are loaded [check Python installation](https://github.com/USEPA/CMAQ/tree/main/PYTOOLS/install)
* Run the Create Ocean File Jupyter Notebook [dmschlo/CMAQ_DMS_ChlorA.ipynb notebook](https://github.com/USEPA/CMAQ/blob/main/PYTOOLS/dmschlo/CMAQ_DMS_ChlorA.ipynb)
* Run the Visualize Ocean File Jupyter Notebook [dmschlo/CMAQ_DMS_ChlorA_Plot.ipynb](https://github.com/USEPA/CMAQ/blob/main/PYTOOLS/dmschlo/CMAQ_DMS_ChlorA_Plot.ipynb)
