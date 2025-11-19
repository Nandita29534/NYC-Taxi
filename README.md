# 🚕 NYC Yellow Cab Analysis: From Hypothesis Testing to Predictive Modeling

This project is a multi-phase data science initiative inspired by the **Google Advanced Data Analytics Certificate** curriculum. Using **2017 NYC Yellow Cab ride records**, the goal was to extract actionable business insights, validate statistical claims, and build predictive machine learning models to improve taxi operations and customer experience.

The workflow progresses from exploratory data cleaning and hypothesis testing to the deployment of **Multiple Linear Regression** and **Classification** models.

---

## 🔍 Key Advanced Skills Demonstrated

### 📊 Statistical Analysis
- Two-Sample t-test  
- Hypothesis Testing  
- A/B Test Interpretation  

### 🤖 Modeling & Machine Learning
- Multiple Linear Regression  
- Outlier Management (IQR, capping using real-world intuition)  
- Feature Engineering  
- Random Forest & XGBoost  
- Residual Analysis  
- Model Selection via F1-Score  

### 🧹 Data Strategy
- Robust data cleaning based on statistical thresholds  
- Removal/capping of unreasonable trip distances, fares, and durations  

### ⚖️ Ethics in AI
- Identifying potential bias  
- Rescoping ML objectives to avoid social harm  

---

## 🛠️ Data, Tools, and Repository Structure

| Category | Details |
|---------|---------|
| **Data Source** | NYC Yellow Cab Ride Records (2017) |
| **Environment** | Python (Jupyter Notebook) |
| **Libraries** | Pandas, NumPy, Matplotlib, Seaborn, Statsmodels, Scikit-Learn, XGBoost |
| **Focus Areas** | EDA, Hypothesis Testing, Regression, Classification, Ethical AI |

### 📁 Repository Contents

| Notebook | Focus Area | Highlight |
|---------|-------------|-----------|
| `01_Automatidata_EDA.ipynb` | Initial EDA | Comprehensive outlier detection & cleaning strategy |
| `02_Automatidata_Statistics.ipynb` | Inferential Statistics | Two-sample t-test for fare difference |
| `03_Automatidata_Regression.ipynb` | Regression Modeling | Multiple Linear Regression, feature engineering, residual analysis |
| `04_Automatidata_ML_Tips.ipynb` | Machine Learning | XGBoost/RF classification & ethical model redesign |

---

# 1️⃣ Phase 1: Statistical Validation (A/B Test Analysis)

### 🎯 Objective  
Determine whether payment type (credit vs. cash) affects the average fare amount.

### 🧪 Hypotheses  
- **H₀ (Null):** No difference in average fare between credit card and cash payments  
- **Hₐ (Alternative):** There *is* a statistically significant difference  

### 📈 Result  
- Two-sample t-test yielded **p-value < 0.05**

### ✅ Conclusion  
**Rejected the null hypothesis.**  
There is a statistically significant difference in average fare amount between credit card and cash-paying customers.

---

# 2️⃣ Phase 2: Predictive Modeling – Multiple Linear Regression

### 🎯 Objective  
Predict taxi **fare amount** using engineered and cleaned features.

### 🧹 Data Preparation  
- Detection and capping of extreme values in distance, fare, and trip time  
- Cleaning guided by domain knowledge (NYC travel norms) + statistical bounds

### ⚙️ Feature Engineering  
- Added `mean_distance`  
- Evaluated impact of engineered features on model performance

### 📊 Model Performance  
| Metric | Value |
|--------|--------|
| **R²** | **0.821** (Model explains 82% variance in fare amount) |
| **RMSE** | **4.45** |

### 🔍 Residual Diagnostics  
- Residuals approx. normal  
- Mean of residuals near zero  
- No major heteroscedasticity issues

### ⭐ Key Insight  
**`mean_distance` emerged as the strongest predictor** in the final regression model.

---

# 3️⃣ Phase 3: Ethical ML Classification – Predicting Generous Tippers

### 🎯 Initial Goal  
Predict customers who **will not** leave a tip.

### ⚠️ Ethical Concerns  
- Could lead to discrimination  
- Risk of service denial based on predicted behavior  
- Negative customer experience & fairness concerns  

### ✅ Ethical Revision  
Model was reframed to:  
> **Predict generous customers (tips ≥ 20%) instead of non-tippers.**

This avoids denial of service and helps drivers identify potential high-earning trips.

### ⚙️ Feature Engineering  
- Created `tip_percent`  
- Generated time-based features (rush hour, morning, night flags)

### 📌 Model Selection  
Chosen metric: **F1-score**  
- Balances both false positives & false negatives  
- Best for scenarios where precision & recall are equally important

### 🤖 Models Used  
- **Random Forest Classifier**  
- **XGBoost Classifier**  
- Training performed on a **balanced dataset**  

---


