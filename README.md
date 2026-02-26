# custom-Python-functions

**Objective:
****Approximate BIS values from raw EEG data using the Openibis algorithm and explore machine learning-based classification of depth of anesthesia (the brain’s response to anesthetic dose).

EEG-Based BIS Estimation: openibis ML Pipeline
==========================================================
Author  : Melody R. Smith
Created : 2026-02-23
Revised : 2026-02-25

Reference : Connor CW. Open Reimplementation of the BIS Algorithms for Depth
            of Anesthesia. Anesth Analg. 2022;135(4):855–864.
            https://doi.org/10.1213/ANE.0000000000006119
Dataset   : https://figshare.com/articles/dataset/EEG_and_BIS_raw_data/5589841

Pipeline overview
-----------------------------------------
  Step 1 — Load and inspect raw EEG data
  Step 2 — Implement openibis algorithm (Connor 2022) with dataset-specific calibration
  Step 3 — Quality control: descriptive statistics and BIS distribution plots,
            Bland-Altman agreement vs. ground-truth BIS values
  Step 4 — Classify depth of anesthesia
              4a. Openibis threshold-based baseline classifier
              4b. XGBoost with openibis scores only (LOOCV)
              4c. XGBoost with openibis + EEG spectral features (LOOCV)
  Step 5 — Report model performance
  Step 6 — Feature importance: identify most predictive EEG features

Depth-of-anesthesia categories (ground-truth BIS thresholds)
-------------------------------------------------------------
  Awake        : BIS ≥ 80
  Sedated      : BIS 60–79
  Anesthetized : BIS 40–59
  Deep/BS      : BIS < 40

Requirements
------------
  pip install numpy scipy scikit-learn pandas matplotlib xgboost h5py
