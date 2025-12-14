# 🛡️ Credit Card Fraud Detection

**Machine Learning & Deep Learning End-to-End Pipeline**

<p align="left">
  <img src="https://img.shields.io/badge/Python-3.10-blue?logo=python" />
  <img src="https://img.shields.io/badge/Notebook-Jupyter-orange?logo=jupyter" />
  <img src="https://img.shields.io/badge/ML-Sklearn-green?logo=scikitlearn" />
  <img src="https://img.shields.io/badge/DL-TensorFlow-yellow?logo=tensorflow" />
  <img src="https://img.shields.io/badge/LightGBM-3.3.0-brightgreen?logo=leaflet" />
  <img src="https://img.shields.io/badge/Status-Completed-success" />
</p>

---

## 🚨 Problem Statement

Credit card fraud poses a major threat to financial institutions, resulting in:

* Direct monetary losses
* Regulatory risk
* Customer dissatisfaction

However, while detecting fraud is essential, **false alarms (false positives)** are even more damaging:

* Legitimate transactions get declined ❌
* Customers abandon the card (churn) 🚶
* Loss of trust and service fee revenue 💸

👉 **The goal of this project is not only to detect fraud but to minimize false alarms.**
In real-life credit card operations, **reducing customer friction sometimes matters more than catching every fraud case**.

This project builds a balanced fraud detection system optimized for **high recall** (catch fraud) and **low false positives** (avoid blocking customers).

---

## 📦 Overview

This repository contains a full end-to-end fraud detection pipeline using the **Kaggle ULB dataset**, including:

* 🔍 Exploratory Data Analysis
* 🧼 Preprocessing, scaling, and SMOTE
* 🤖 Baseline & advanced ML models
* 🧠 Deep learning MLP models
* 📊 Excel-based logistic regression (explainability)
* 📈 Model comparison
* 🧾 Business impact interpretation
* 🚧 Limitations & future work
---

## 📂 Project Structure

```
fraud-detection/
│
├── data/
│   └──README.md                        
│
├── notebook/
│   └── fraud_detection_full_pipeline.ipynb
│
├── excel/
│   ├── LR_excel.xlsx
│   └── README.md
│
├── outputs/
│   ├── figures/
│   ├──feature_importance/      
│   └── models/         
│
├── README.md
└── requirements.txt
```

---
# 📊 Dataset

**Source:** [https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

* **Rows:** 284,807 transactions
* **Fraud cases:** 492 (0.172%)
* **Features:** PCA components (V1–V28), *Time*, *Amount*
* **Target:**

  * `0` — normal
  * `1` — fraud

It is **highly imbalanced**, requiring special handling through:

* SMOTE
* Class weights
* Threshold tuning

---

# 🔍 Exploratory Data Analysis (EDA)

Includes:

* Class distribution visualization
* Transaction amount patterns
* Correlation heatmaps
* PCA component distribution
* Outlier analysis

---

# 🧼 Preprocessing

* Remove unnecessary columns
* Stratified train-test split
* Scale **Time** and **Amount** using `StandardScaler`
* Apply **SMOTE only on training set** (Logistic Regression only)
* Export scaled + SMOTE datasets to Excel

---

# 🤖 Machine Learning Models

### 1️⃣ Logistic Regression (with SMOTE + threshold tuning)

⭐ Most interpretable & best suited for regulated financial environments.

### 2️⃣ Random Forest

✔ Handles non-linear features
✔ Built-in feature importance

### 3️⃣ LightGBM

⚡ Fast and highly accurate
✔ Handles imbalance with built-in parameters

---

# 🧠 Deep Learning Models

### 4️⃣ Shallow MLP

* 1–2 dense layers
* Fast and simple baseline

### 5️⃣ Deep MLP

* Multiple dense layers
* More learning capacity

---

# 🏆 Model Performance Summary

*(Replace these placeholders with your final numbers.)*

| Model                        | ROC-AUC   | PR-AUC   | Recall (Fraud) | False Alarm Rate | Notes                        |
| ---------------------------- | --------- | -------- | -------------- | ---------------- | ---------------------------- |
| **Logistic (SMOTE + tuned)** | **0.973** | **0.71** | **0.82**       | **Very Low**     | Best business-friendly model |
| LightGBM                     | 0.98      | 0.70     | 0.80           | Low              | High performance             |
| Deep MLP                     | 0.98      | 0.72     | 0.81           | Medium-Low       | Strong nonlinear learner     |
| Shallow MLP                  | 0.97      | 0.68     | 0.78           | Medium           | Good baseline                |
| Random Forest                | 0.96      | 0.65     | 0.75           | Medium-High      | Overfits slightly            |

---

# 📈 Business Interpretation

### ✔ Catch as much fraud as possible

Fraud is costly — every undetected fraud is a direct loss.

### ✔ But false alarms cost even more

False positives cause:

* Customer dissatisfaction
* Lost revenue
* Declined transactions
* Customer churn

Banks often accept a small amount of fraud to maintain good customer experience.

This project focuses on **tuning probability thresholds** to find the optimal business trade-off.

---

# 🧾 Explainability (Excel Version)

To meet audit & regulatory requirements:

* Export preprocessed + SMOTE training data to Excel
* Train Logistic Regression in Excel using RegressIt
* Compare:

  * Coefficients
  * Odds ratios
  * Feature contributions
  * Probability threshold

This ensures transparent, regulator-friendly modeling.

---

# ⚠️ Limitations

* Dataset uses PCA-transformed data → limits interpretability
* SMOTE may introduce synthetic noise
* Fraud patterns change over time (concept drift)
* No cost-sensitive learning (fraud cost ≠ false alarm cost)
* Deep learning not optimized for latency in real-time credit systems

---

# 🚀 Future Work

* Use raw non-PCA features for better interpretability
* Add SHAP for full explainability
* Cost-sensitive loss functions
* Deploy real-time API (FastAPI + Docker)
* Try anomaly detection methods
* Use sequential models (LSTM, Transformers)

---

# 🛠 Installation

```bash
pip install -r requirements.txt
```

---

# ▶️ Running the Pipeline

Open the main notebook:

```
notebook/fraud_detection_full.ipynb
```



---

# 🙌 Acknowledgements

Dataset by **Université Libre de Bruxelles (ULB)** Machine Learning Group.


