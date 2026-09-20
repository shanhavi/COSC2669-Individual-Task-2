# COSC2669 Individual Task 2 – EEG Analysis

## Purpose

This repository provides reproducible supporting evidence for COSC2669 Individual Task 2. It evaluates KNN and SVM models using the BEED and EEG Eye State datasets, with additional analysis of temporal leakage, learning curves and Fairlearn `MetricFrame` group comparisons.

## Datasets

* [BEED: Bangalore EEG Epilepsy Dataset](https://archive.ics.uci.edu/dataset/1134/beed%3A%2Bbangalore%2Beeg%2Bepilepsy%2Bdataset)
* [EEG Eye State Dataset](https://archive.ics.uci.edu/dataset/264/eeg+eye+state)

The original datasets are not included in this repository. To reproduce the analysis, download them, name them `BEED_Data.csv` and `EEG Eye State.arff`, and place them beside the notebook.

## Evaluation Approach

* BEED uses a stratified 80/20 train-test split and four-fold stratified cross-validation.
* EEG Eye State uses groups of 128 consecutive records to reduce leakage between neighbouring observations.
* Preprocessing is fitted inside each model pipeline using training data only.
* Macro-F1 is the primary model-performance metric.
* Fairlearn compares performance across BEED target classes and EEG recording periods.
* These comparisons assess class-wise and temporal consistency, not demographic fairness.

## Repository Contents

* `COSC2669_Task2_EEG_Fairness_Analysis.ipynb` – complete reproducible analysis.
* `eye_state_split_sensitivity.png` – random-row versus blocked-group comparison.
* `learning_curves.png` – training and validation performance across training-set sizes.
* `fairlearn_group_performance.png` – group-performance comparisons.
* CSV files – numerical evidence supporting the learning-curve, temporal and Fairlearn results.

## Running the Notebook

Install the required packages:

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn fairlearn jupyter
```

Open `COSC2669_Task2_EEG_Fairness_Analysis.ipynb` and run all cells from beginning to end.

## Limitations

BEED does not provide subject identifiers, so patient-independent evaluation cannot be confirmed. EEG Eye State contains sequential observations from a limited recording, and blocked grouping reduces but does not eliminate temporal dependence. Neither dataset contains demographic attributes such as age, gender or ethnicity; therefore, this analysis does not claim demographic fairness or clinical validation.
