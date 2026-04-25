# 🧠 Explainable AI (XAI) for Cancer Prediction

An end-to-end machine learning pipeline focused on **interpretability** and **trustworthiness** in medical diagnostics. This project predicts breast cancer using the Wisconsin Dataset and explains every decision using state-of-the-art XAI techniques.

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-black?style=flat-square)](https://xgboost.ai/)
[![XAI](https://img.shields.io/badge/XAI-SHAP%20%26%20LIME-red?style=flat-square)](https://github.com/slundberg/shap)

---

## 📌 Overview

In healthcare, a "Black Box" model is often unacceptable. Clinicians need to know **why** a model flagged a patient as high-risk. This project addresses this by:
1.  Training high-accuracy classifiers (Random Forest & XGBoost).
2.  Deconstructing predictions into human-readable feature contributions.
3.  Providing both **Global** (how the model works overall) and **Local** (why this specific patient) explanations.

---

## 📊 Dataset

**Breast Cancer Wisconsin (Diagnostic)**
* **Samples**: 569
* **Features**: 30 numerical attributes (Mean, Standard Error, and "Worst" values for radius, texture, perimeter, area, smoothness, etc.)
* **Target**: 
    * `0`: Benign (Non-cancerous)
    * `1`: Malignant (Cancerous)

---

## ⚙️ Installation

To get started, clone this repository and install the required dependencies:

```bash
pip install shap lime xgboost scikit-learn matplotlib seaborn
```

---

## 🚀 The Pipeline

1.  **Data Ingestion**: Loading and scaling 30 numerical nuclear features.
2.  **Training**: Benchmarking Random Forest vs. XGBoost.
3.  **Evaluation**: Focus on **Recall** (minimizing False Negatives) and **ROC-AUC**.
4.  **XAI Integration**: Applying SHAP and LIME to the best-performing model.

---

## 🤖 Model Performance

The model achieves near-perfect diagnostic capability:

| Metric | Score |
| :--- | :--- |
| **Accuracy** | ≈ 96% |
| **ROC-AUC** | ≈ 0.99 |

### Confusion Matrix Insight
```text
[[40  3]   <- Benign
 [ 2 69]]  <- Malignant
```
> **Critical Note**: With only 2 False Negatives, the model ensures that very few malignant cases go undetected, which is the top priority in clinical screening.

---

## 🧠 Explainable AI (XAI) Methods

### 1. SHAP (SHapley Additive exPlanations)
SHAP uses game theory to assign each feature an importance value for a particular prediction.



* **Global Summary**: Visualizes which features (like `mean concave points`) most strongly drive the model's global decisions.
* **Local Force Plot**: Explains a single patient's prediction as a mathematical sum: 
$$prediction = base\_value + \sum SHAP\_values$$

### 2. LIME (Local Interpretable Model-agnostic Explanations)
LIME creates a simplified, local linear model around a specific prediction to explain its behavior.



* **Insight**: Shows exactly which feature values "voted" for Malignant vs. Benign for a specific individual.

---

## 🔬 Why This Matters

* **Clinical Trust**: Allows doctors to verify if the AI is looking at the correct medical markers.
* **Vulnerability Detection**: Identifies if the model is relying on "noise" or biases in the data.
* **Feature Discovery**: Helps researchers identify which cell nucleus characteristics are the strongest indicators of malignancy.

---

## 📂 Project Structure
```text
Explainable-AI-Cancer/
 ┣ 📜 Explainable_AI_for_cancer_prediction.ipynb # Full Pipeline
 ┣ 📜 README.md                                  # Documentation
 ┣ 📂 outputs/                                   # SHAP & LIME Plots
 ┗ 📜 model_checkpoint.pkl                       # Trained XGBoost model
```

---

## 👨‍💻 Author
**Phat**
*Passionate about Research in Computer Vision, XAI, and Multimodal Image Processing.*

---
*Built with ❤️ to bridge the gap between AI performance and Medical Trust.*
