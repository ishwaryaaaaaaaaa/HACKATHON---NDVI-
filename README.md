# 🛰️ NDVI-Based Land Cover Classification using Logistic Regression

This project tackles the challenge of classifying **land cover types** using **NDVI time-series data** derived from satellite imagery, aligned with **OpenStreetMap (OSM) labels**. NDVI values tend to be noisy due to atmospheric conditions, seasonal shifts, and data resolution — but the goal is to build a **robust Logistic Regression model** that accurately predicts the correct land cover class. 🌍

---

## 📌 Problem Statement

> Predict the **type of land cover** (e.g., forest, urban, water, cropland, etc.) using time-series NDVI data and ground-truth labels from OSM.

---

## 🧾 Dataset Description

- **Features**: NDVI values captured across multiple timestamps.  
  Format: `ndvi_1`, `ndvi_2`, ..., `ndvi_n`
- **Target**: Land cover class (multi-class categorical variable from OSM annotations).
- **Challenge**: NDVI time series are noisy and overlapping across classes.

---

## 🛠️ Approach

1. **Data Preprocessing**
   - Handled missing or corrupted NDVI values.
   - Normalized NDVI time-series per sample.
   - Optional: Denoising via moving average or smoothing (e.g., Savitzky–Golay).

2. **Feature Engineering**
   - Extracted statistical features from NDVI series:
     - Mean, standard deviation, min, max
     - Seasonal trends (early/late growth)
     - Number of peaks or dips (if smoothed)

3. **Modeling: Logistic Regression**
   - Multi-class logistic regression (Softmax version)
   - One-vs-rest strategy (if needed)
   - L2 regularization to prevent overfitting on noisy inputs

4. **Evaluation**
   - Accuracy, macro F1-score
   - Confusion matrix to analyze per-class performance

---

##  Why Logistic Regression?

✅ Simple and interpretable  
✅ Fast to train and tune  
✅ Performs well on **linearly separable** or near-separable features  
✅ Serves as a **strong baseline** before using complex models (like XGBoost or CNNs)

---


## 🔄 Model Workflow (Mermaid)

```mermaid
graph TD
    A[NDVI Time-Series Data] --> B[Preprocessing & Denoising]
    B --> C[Feature Engineering]
    C --> D[Logistic Regression Model]
    D --> E[Predicted Land Cover Type]
