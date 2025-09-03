# 📊 Telco Customer Churn Prediction

## 📌 Project Overview
Customer churn is a major challenge for telecommunications companies as retaining existing customers is often more cost-effective than acquiring new ones.  
This project aims to **predict customer churn** by building and evaluating machine learning models, enabling businesses to proactively identify at-risk customers and implement targeted retention strategies.

---

## 🏷 Problem Definition
The objective is to develop a **predictive model** that classifies customers as either **churners** or **non-churners**, allowing the business to focus retention efforts on customers most likely to leave.

---

## 🛠 Data Preprocessing
- **Dataset:** Telco Customer Churn Dataset  
- **Cleaning Steps:**
  - Converted blank `'TotalCharges'` values to NaN and dropped affected rows.
  - Separated features (`X`) and target (`y`).
  - Identified categorical and numerical features.
- **Preprocessing Pipeline:**
  - Used `ColumnTransformer` to apply:
    - `StandardScaler` → Numerical features
    - `OneHotEncoder` → Categorical features
  - Excluded `'customerID'` column.
  - Ensured consistent preprocessing for training and future predictions.

---

## 🤖 Model Development
Two models were selected:
- **Logistic Regression**
- **Random Forest Classifier**

Each model was wrapped in a pipeline that included preprocessing + classifier.  
The issue with `'customerID'` was resolved by dropping it explicitly from `X`.

---

## 🎯 Hyperparameter Tuning
Used **GridSearchCV** with 5-fold cross-validation and `accuracy` scoring:
- **Logistic Regression Best Params:** `{'classifier__C': 100}`
- **Random Forest Best Params:** `{'classifier__max_depth': 10, 'classifier__n_estimators': 200}`

---

## 📈 Model Evaluation
Evaluated the best models on training data using Accuracy, Precision, Recall, and F1-Score:

| Model               | Accuracy | Precision | Recall | F1-Score |
|--------------------|---------|-----------|--------|---------|
| Logistic Regression | 0.8062 | 0.6611    | 0.5554 | 0.6037 |
| Random Forest       | **0.8645** | **0.7951** | **0.6602** | **0.7214** |

✅ **Random Forest outperformed Logistic Regression across all metrics**.

---

## 🔍 Key Insights
- **Random Forest** provides:
  - Higher accuracy → Better overall predictions
  - Higher precision → More reliable churn predictions
  - Higher recall → Better identification of actual churners
  - Higher F1-Score → Best balance between precision & recall
- **Reason for better performance:** Random Forest captures **non-linear relationships** and **feature interactions** better than Logistic Regression.

---

## 🏆 Preferred Model
The **Random Forest Classifier** was chosen as the final model due to its superior performance and better balance between precision and recall.

---

## 💾 Model Export
The **best-performing Random Forest pipeline** was exported using `joblib` for deployment.

---

