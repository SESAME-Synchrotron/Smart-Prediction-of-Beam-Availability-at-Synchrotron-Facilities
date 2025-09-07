# MFP
SESAME's Machine Fault Prediction -- (Smart Prediction of Beam Availability at Synchrotron Facilities)

# What is MFP
It is a project that aims to develop a smart system  that is integrated with different information sources at SESAME Synchrtotron to predict beam faults / interubts before they actually occur.

# Metadata Description

All metadata comes as files under folder metadata directory, the list of files is shown below: 
<ul>
  <li>"metadata\1- Machine Statistic V8-2.xlsx": This Excel file contains machine operation statistics from SESAME spanning March 2020 – December 2023. It provides detailed logs of trip events recorded by synchrotron operators, serving as the foundation for the predictive modeling conducted in this study.</li>
  <li>"metadata\2- Features_List of PVs_v0.2.xlsx": This Excel file lists the Process Variables (PVs) considered in the study. It includes the identifiers and descriptions of PVs archived at SESAME that were evaluated as candidate features for predictive modeling. Out of an initial set of 263 PVs, a consistent subset of 169 PVs (common across 2020–2023) was selected in consultation with domain experts. the file helps users understand the signals contributing to the predictive models.</li>
  <li>"metadata\3- Machine Statistic_CleanStatisticsWithExactTripTime": This CSV file contains the validated trip statistics with exact timestamps refined from operator logs. Using the ±3-minute search and largest-drop method described in the paper, each trip time was corrected to align with the true event captured in the PV data. This cleaned dataset ensures accurate alignment of trip events with corresponding PV signals and forms a crucial input for building the labeled time-window datasets.</li>
</ul>

# Dataset Description

This repository hosts a sample dataset used in the paper “Smart Prediction of Beam Availability at Synchrotron Facilities”.
The full dataset is openly available on Zenodo:

# DOI

10.5281/zenodo.17074063
Please cite this DOI if you use the dataset in your research.



