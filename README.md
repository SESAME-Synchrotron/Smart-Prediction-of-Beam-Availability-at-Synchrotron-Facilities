# Smart Prediction of Beam Availability at Synchrotron Facilities
SESAME's Machine Fault Prediction -- (Smart Prediction of Beam Availability at Synchrotron Facilities)

# Introduction
It is a project that aims to develop a smart system  that is integrated with different information sources at SESAME Synchrtotron to predict beam faults / interubts before they actually occur.

The dataset presents a data-driven approach to improving the reliability of synchrotron operations. At the heart of this work is the creation of a carefully curated dataset built from SESAME’s machine operation records between March 2020 and December 2023. The dataset combines operator-logged trip events with stable no-trip intervals, capturing the dynamics of machine performance over several years. A large pool of more than 16,800 Process Variables (PVs) was originally archived through SESAME’s EPICS control system. With the guidance of domain experts, this pool was narrowed down to 263 meaningful signals, and then further refined to 169 PVs that were consistently available across all years. Each recorded trip event was validated by aligning operator logs with the actual machine data in the EPICS Archiver, ensuring accurate timestamps through a ±3-minute search and drop detection method. To account for differences in PV sampling strategies (event-driven vs. scanned signals). Using this pipeline, the dataset was expanded into multiple time-windowed samples (10 to 300 seconds), each labeled as either a trip or a no-trip event. The resulting dataset, with more than 200,000 labeled windows, represents a unique resource for developing and benchmarking machine learning and deep learning models in synchrotron reliability research.

- Start data collection date:  March 2024 
- End data collection date:  March 2024 

# Metadata Description

All metadata comes as files under folder metadata directory, the list of files is shown below: 

  - **metadata\1- Machine Statistic V8-2.xlsx**: This Excel file contains machine operation statistics from SESAME spanning March 2020 – December 2023. It provides detailed logs of trip events recorded by synchrotron operators, serving as the foundation for the predictive modeling conducted in this study.
  - **metadata\2- Features_List of PVs_v0.2.xlsx**: This Excel file lists the Process Variables (PVs) considered in the study. It includes the identifiers and descriptions of PVs archived at SESAME that were evaluated as candidate features for predictive modeling. Out of an initial set of 263 PVs, a consistent subset of 169 PVs (common across 2020–2023) was selected in consultation with domain experts. the file helps users understand the signals contributing to the predictive models.
  - **metadata\3- Machine Statistic_CleanStatisticsWithExactTripTime**: This CSV file contains the validated trip statistics with exact timestamps refined from operator logs. Using the ±3-minute search and largest-drop method described in the paper, each trip time was corrected to align with the true event captured in the PV data. This cleaned dataset ensures accurate alignment of trip events with corresponding PV signals and forms a crucial input for building the labeled time-window datasets.

# Dataset Description

This repository hosts a sample dataset used in the paper “Smart Prediction of Beam Availability at Synchrotron Facilities”.
The full dataset is openly available on Zenodo:

# DOI

10.5281/zenodo.17074063

> Please cite this DOI if you use the dataset in your research.



