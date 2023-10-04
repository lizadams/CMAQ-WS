---
title: Run Jupyter Notebook to analyze difference between with DESID Emissions and the base case (no emission reduction)
weight: 30 
---

###  Connect to the NICE DCV 

1. Select Activities, then click on Terminal Image (MATE Terminal)

2. Change directories to the location of the Jupyter Notebook 

```csh
cd /shared/pcluster-cmaq/qa_scripts/workshop
```

3. Switch to the .tcsh shell

```csh
/bin/tcsh
```

4. Run Jupyter Notebook  (this may take a few minutes to run and to start the firefox browser)

```csh
jupyter notebook
```


5. Double Click on the Spatial_Plots_of_Ave_Conc_Differences.ipynb notebook

![jupyter notebook](/static/images/5-jupyter-notebook-avg-conc-diff.png)

6. In each cell you can use the 'shift return'  or 'shift enter' to run each cell

7. In the section "Set up your Inputs" you will use shift+enter, then enter the value, and then enter to submit the answer.

8. View the plots within the Jupyter Notebook in cells after the plots have been generated 

9. Plot of Average SO2 Base (left plot) versus Average SO2 DESID REDUCE CMAQ

![maximum negative decrease in SO2 Concentration](/static/images/6-SO2-average-base-vs-desid.png)

10. Plot of maximum negative decrease in ASO4J Concentration

![maximum negative decrease in ASO4J Concentration](/static/images/6-SO2-diff-vs-perc-diff.png)
