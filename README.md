# Mini_Project_Python_Med
ML mini project
# MAGIC Gamma Telescope Classification

This repository contains a machine learning workflow that analyzes and classifies data from the **MAGIC (Major Atmospheric Gamma Imaging Cherenkov) Telescope dataset** (`magic04.data`). 

The objective is to classify simulated patterns of high-energy gamma particles (`g`) versus hadronic background noise (`h`) based on the geometric characteristics of the atmospheric Cherenkov showers.

---

## Features & Workflow

The project is structured within a Python script pipeline that handles everything from raw data ingestion to model comparison:

* **Data Cleaning & Preprocessing**:
  * Automatically applies the standard dataset column headers.
  * Handles data type conversions, strips trailing spaces, and drops duplicate records.
  * Detects and removes outliers across all 10 numerical features using the **Interquartile Range (IQR)** method.
  * Encodes the categorical target class (`g` $\rightarrow$ `1`, `h` $\rightarrow$ `0`).
* **Feature Scaling**:
  * Splits data using a stratified 80/20 train/test split to preserve class ratios.
  * Standardizes features using `StandardScaler` to ensure optimal performance for linear models.
* **Model Training & Evaluation**:
  * Trains and evaluates a **Logistic Regression** baseline.
  * Trains and evaluates a **Decision Tree Classifier** ($max\_depth=10$).
  * Generates visual data insights, such as distribution comparison plots and confusion matrix heatmaps using `Seaborn` and `Matplotlib`.

---

## Dataset Overview

The model trains on 10 continuous geometric features extracted from the telescope images:

| Feature Name | Description |
| :--- | :--- |
| `fLength` | Major axis of ellipse [mm] |
| `fWidth` | Minor axis of ellipse [mm] |
| `fSize` | 10-log of sum of content of all pixels [in photons] |
| `fConc` | Ratio of sum of two highest pixels to fSize |
| `fConc1` | Ratio of highest pixel to fSize |
| `fAsym` | Distance from highest pixel to center, projected onto major axis [mm] |
| `fM3Long` | 3rd root of third moment along major axis [mm] |
| `fM3Trans` | 3rd root of third moment along minor axis [mm] |
| `fAlpha` | Angle of major axis with vector to source [deg] |
| `fDist` | Distance from origin to center of ellipse [mm] |
| `class` | **Target:** `g` (gamma signal, encoded as 1) or `h` (hadronic background, encoded as 0) |

---

## Results & Conclusion

After evaluating both models on the processed test partition, the final accuracies achieved were:

* **Logistic Regression Model:** `79.62%`
* **Decision Tree Classifier Model:** `82.33%`

> **Conclusion:** The **Decision Tree Classifier** outperformed the Logistic Regression baseline by capturing non-linear relationships and thresholds within the Cherenkov shower geometric features.

---
