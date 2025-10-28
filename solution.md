# Cardiomegaly Prediction

## Problem Overview
The goal of this project is to build a model using **classical Machine Learning** methods that predicts whether a patient suffers from hypertrophic cardiomyopathy (`Cardiomegaly`) based on numerical features describing heart and lung size, shape ratios, and geometric indicators of heart structure.

The target column `Cardiomegaly` indicates the diagnosis outcome:

- `1` → the patient suffers from Cardiomegaly  
- `0` → the patient does not suffer from Cardiomegaly  

By analyzing these features, we aim to **uncover patterns** associated with the presence of cardiomegaly and evaluate model performance on unseen patient data.

---

## Dataset
- Number of records: 37  
- Number of selected features: 9 numerical features from 12
- Dataset split: 80% training, 20% testing  

Before training, all features are standardized to ensure comparability.

---

## Model Selection

Due to the **small size of the dataset**, certain models are more suitable than others.

### 1. Support Vector Machine (SVM)
- Works well with **small datasets**  
- Effective in **high-dimensional spaces**  
- Can handle **nonlinear relationships** using RBF kernel  

**Parameters used:**
- Kernel: RBF  
- Regularization (C): 2  
- Gamma: 'scale'  
- Class weight: None  

### 2. Logistic Regression (LR)
- Works well for approximately **linear relationships**  
- L1 regularization helps **reduce overfitting**

**Parameters used:**
- Penalty: L1  
- Regularization (C): 5  
- Solver: liblinear  
- Max iterations: 1000  
- Class weight: None  

### 3. Models Rejected
- **Decision Tree:** prone to overfitting with small datasets  
- **k-Nearest Neighbors:** sensitive to feature scaling and noise  
- **Random Forest:** limited effectiveness with only 37 samples  

---

## Results

| Classifier | Accuracy (CV Mean) | Accuracy (Test) | Precision (Test) | Recall (Test) | F1-score (Test) |
|-------------|-------------------|-----------------|------------------|----------------|-----------------|
| **Support Vector Machine (SVM)** | **82.4%** | **75.0%** | **75.0%** | **100.0%** | **85.7%** |
| **Logistic Regression** | **79.2%** | **62.5%** | **71.4%** | **83.3%** | **76.9%** |

- **SVC performed better** than Logistic Regression on this dataset.  
- High recall (1.0) of SVC indicates all positive cases were **correctly identified**, which is critical in a medical diagnosis context.  
- Logistic Regression performed slightly worse in both precision and recall.

---

## Final Remarks
- Small dataset size limits maximum achievable accuracy.  
- SVC’s ability to capture nonlinear patterns makes it **more suitable** for this task.  
- High recall is desirable to avoid missing positive Cardiomegaly cases.  
- Results highlight the challenges of training reliable models on limited data.
