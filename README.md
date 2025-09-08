# Smart Prediction of Beam Availability at Synchrotron Facilities
SESAME's Machine Fault Prediction -- (Smart Prediction of Beam Availability at Synchrotron Facilities)

## Introduction
This project aims to develop a smart system  that is integrated with different information sources at SESAME Synchrtotron to predict beam faults / interubts before they actually occur.

The dataset presents a data-driven approach to improving the reliability of synchrotron operations. At the heart of this work is the creation of a carefully curated dataset built from SESAME’s machine operation records between March 2020 and December 2023. The dataset combines operator-logged trip events with stable no-trip intervals, capturing the dynamics of machine performance over several years. A large pool of more than 16,800 Process Variables (PVs) was originally archived through SESAME’s EPICS control system. With the guidance of domain experts, this pool was narrowed down to 263 meaningful signals, and then further refined to 169 PVs that were consistently available across all years. Each recorded trip event was validated by aligning operator logs with the actual machine data in the EPICS Archiver, ensuring accurate timestamps through a ±3-minute search and drop detection method. To account for differences in PV sampling strategies (event-driven vs. scanned signals). Using this pipeline, the dataset was expanded into multiple time-windowed samples (10 to 300 seconds), each labeled as either a trip or a no-trip event. The resulting dataset, with more than 200,000 labeled windows, represents a unique resource for developing and benchmarking machine learning and deep learning models in synchrotron reliability research.

- Start data collection date:  March 2024
- End data collection date:  June 2024 

## Metadata Description

All metadata comes as files under folder metadata directory, the list of files is shown below: 

  - **metadata\1- Machine Statistic V8-2.xlsx**: This Excel file contains machine operation statistics from SESAME spanning March 2020 – December 2023. It provides detailed logs of trip events recorded by synchrotron operators, serving as the foundation for the predictive modeling conducted in this study.
  - **metadata\2- Features_List of PVs_v0.2.xlsx**: This Excel file lists the Process Variables (PVs) considered in the study. It includes the identifiers and descriptions of PVs archived at SESAME that were evaluated as candidate features for predictive modeling. Out of an initial set of 263 PVs, a consistent subset of 169 PVs (common across 2020–2023) was selected in consultation with domain experts. the file helps users understand the signals contributing to the predictive models.
  - **metadata\3- Machine Statistic_CleanStatisticsWithExactTripTime**: This CSV file contains the validated trip statistics with exact timestamps refined from operator logs. Using the ±3-minute search and largest-drop method described in the paper, each trip time was corrected to align with the true event captured in the PV data. This cleaned dataset ensures accurate alignment of trip events with corresponding PV signals and forms a crucial input for building the labeled time-window datasets.

> This repository hosts a ***sample*** dataset used in the paper “Smart Prediction of Beam Availability at Synchrotron Facilities”.
The ***full dataset*** is openly available on <a href="https://zenodo.org/records/17074063">Zenodo</a>.

## Dataset Describtion

When browsing the dataset, detailed column descriptions can be found in the file **metadata/2- Features_List of PVs_v0.2.xlsx**, which documents the Process Variables (PVs) included in the study.
- The **pvData/** directory contains two main subfolders:
  - trip_raw/: This folder includes trip-event data that has been filtered and validated against operator logs. The raw operator-reported statistics were cleaned, corrected, and aligned with the actual machine signals from the EPICS archiver to ensure precise timestamps and reliable labels.
  - noTrip_raw/: This folder contains samples of stable machine operation, randomly collected from the EPICS archiver between 2022 and 2024 during periods of full and reliable beamtime. These no-trip intervals serve as the negative class examples (label = 0) in the predictive modeling.
Together, these two data sources form the foundation of the dataset, enabling the construction of balanced, labeled windows (trip vs. no-trip) that are essential for training and evaluating machine learning and deep learning models.

- Each of the subfolders under pvData/trip_raw and pvData/noTrip_raw contains 10 additional subfolders, named **WS_XX**, where XX represents the time-window size in seconds. The available windows are 10, 20, 30, 40, 50, 60, 120, 180, 240, and 300 seconds.
  - For trip data, each WS_XX folder includes PV samples extracted for the given number of seconds before the exact validated trip timestamp.
  - For no-trip data, the WS_XX folders store PV samples collected during stable operation, with the same time-window sizes applied, ensuring consistency with the trip dataset.

- Each subfolder (**WS_XX**) contains a set of CSV files named using the convention:
- > YYYYMMDDTHHMMSS.csv, For example: 20231203T192156.csv 
The date and time stamp in the filename indicates the exact event time:
- For trip data, this corresponds to the validated timestamp of a beam interruption.
- For no-trip data, it marks the precise moment when the sample of stable operation was collected.
This means every file can directly traced back to its collection time, enabling reproducibility and chronological analyses. 

- When opening a CSV file, some columns may contain the tag **NATRD**, which indicates that no data was available for that PV at the collection time. This can occur for several reasons:
  - A device was not yet installed or in use at SESAME during the given year (e.g., unavailable in 2022 but operational and archived from 2023 onwards).
  - A PV was not being archived at that time but was added to the EPICS archiver in later years.

### Important Notes About Dataset 

It is important to note that the dataset is not balanced between trip and no-trip events. Trip events, which represent actual beam interruptions, are naturally ***less frequent*** compared to the long periods of stable operation (no-trip). For example, over the collection period 2020–2023, only 222 validated trip events were identified, whereas thousands of no-trip intervals were available. This imbalance reflects the real operational environment of the synchrotron, where beam interruptions are rare but critical. In addition, the number of rows per file ***is not uniform***, since it depends on how each PV was archived. Monitored PVs are recorded only when their values change (event-driven), while scanned PVs are archived at fixed sampling rates (e.g., 10 readings per second). As a result, some files contain denser time series than others. Users of the dataset should take these characteristics into account when training models. 

## Cite This Dataset 

If you use this dataset in your research, please cite it as:
***Alzubi, M., Abbadi A., Ghnemat, R., & Al Madi, N. (2025). SESAME Beam Availability Dataset [SESAME Machine Dataset]***. ***Zenodo. https://doi.org/10.5281/zenodo.17074063***
