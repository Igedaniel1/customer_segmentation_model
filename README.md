# 📊 **Customer Default Prediction Project**

## 🎯 **Objective**

Predict whether a customer will default using features like **Age**, **Income**, **Debt**, **Years Employed**, etc.  
This is a **binary classification** task with **class imbalance** (fewer defaulters than non-defaulters).

---

## 🧹 **1. Data Cleaning**

- Filled missing values in the `Defaulted` column using the **mode** to prevent training errors.

---

## 📈 **2. Exploratory Data Analysis (EDA)**

- Used **boxplots** to visualize feature distributions by default status.
- Created a **correlation heatmap**. Found that `DebtIncomeRatio` had the highest correlation (~0.36) with defaulting.

---

## 🛠 **3. Feature Engineering**

- Applied **log transformation** to skewed features like income and debt.
- Engineered new features:  
  - `TotalDebt` = CardDebt + OtherDebt  
  - `IncomePerYearEmployed` = Income / YearsEmployed

---

## 🧪 **4. Data Splitting & Imbalance Handling**

- Used **stratified train-test split** to preserve class ratios.
- Applied **SMOTE** (Synthetic Minority Oversampling Technique) from `imbalanced-learn` to balance training data.
- Handled SMOTE-related errors by removing **NaNs** and ensuring **numeric-only inputs**.

---

## 🤖 **5. Modeling**

- Tried multiple models:
  - `RandomForestClassifier`: for **robustness** and **interpretability**
  - `XGBoostClassifier`: for **performance** on structured/tabular data
  - `HistGradientBoostingClassifier`: for **speed** and built-in handling of **missing values**

---

## 📊 **6. Evaluation Strategy**

- Used metrics:
  - **Accuracy**
  - **Precision**
  - **Recall**
  - **ROC AUC**
- Lowered the default prediction threshold (from 0.5) to improve **recall**, as **flagging actual defaulters** is a higher priority.
- Plotted **Precision-Recall** and **ROC curves** for threshold tuning.

---

## 🔍 **7. Checking Predictive Signal**

- Trained the same model on **random labels** → AUC dropped to ~0.41.
- This confirms the original model was learning a **real signal**.
- If AUC had remained high, it would indicate **data leakage** or **overfitting**.

---

## 💡 **Key Observations**

- Feature correlations with the target were **weak**.
- Final model performance plateaued at:
  - **Accuracy**: ~76%
  - **Precision**: ~46%
  - **Recall**: ~65%
  - **ROC AUC**: ~0.80

---

## ✅ **Conclusion**

In this project, I applied thorough **preprocessing**, **feature engineering**, **class balancing**, and **signal validation** to optimize model performance.  
However, the model’s ceiling was limited by the **quality and depth** of the available features.

---

## 📌 **Recommendation**

Since many companies prioritize **recall** (i.e., catching actual defaulters), even at the cost of some **false positives**, this model is suitable for that purpose given the current dataset.

---

## 🔭 **Next Steps**

- I'll improve data quality by collecting additional features:
  - **Credit history**
  - **Payment timelines**
  - **Spending patterns**
- Explore **model explainability tools** (e.g., SHAP).
