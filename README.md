# HEALTH-PREMIUM-PREDICTOR       

# 💡 Health Premium Predictor

Predicting health insurance premium based on personal and lifestyle information using machine learning.

![App Screenshot](Health_premium_predictor_app.png)


---

## 🚀 Motivation

Rising healthcare costs make it critical to accurately estimate health insurance premiums. Insurance companies, agents, and customers benefit from personalized premium predictions. This project uses historical data and machine learning to create a predictive system, reducing manual estimation errors and enhancing accessibility.

---

## 📂 Dataset Information

Although the dataset link is unavailable, the model was trained on a structured dataset with the following features:

- `Age`
- `Gender`
- `Region`
- `Marital_status`
- `Number_Of_Dependants`
- `BMI_Category`
- `Smoking_Status`
- `Employment_Status`
- `Income_Level`
- `Income_Lakhs`
- `Medical_History`
- `Insurance_Plan`
- `Annual_Premium_Amount` *(Target Variable)*

An additional feature `genetical_risk` was engineered from `Medical_History` to enhance prediction accuracy.

---

## 🛠️ Tech Stack & Tools

- Python
- NumPy, Pandas
- Matplotlib, Seaborn
- Scikit-learn
- XGBoost
- Streamlit

---

🧹 Data Preprocessing & Feature Engineering
A robust data preprocessing pipeline was developed to clean, transform, and enrich the dataset before feeding it into machine learning models.

✅ Key Steps in Preprocessing:
Handling Outliers:

Boxplots were used to visualize potential outliers in numerical features.

Outliers in the Income_Lakhs column were removed using the 99.9th percentile threshold:

python
Copy
Edit
quantile_threshold = df.income_lakhs.quantile(0.999)
df = df[df.income_lakhs < quantile_threshold]
Encoding Categorical Features:

Applied one-hot encoding to convert categorical variables into numerical format for model compatibility.

Feature Engineering:
Several new features were created to capture more nuanced relationships:

New Feature Name	Description
age_income_ratio	Ratio of age to income — reflects relative earning capacity.
bmi_smoking_interaction	Interaction term between BMI and smoking status — useful in health modeling.
income_dependents_ratio	Income divided by number of dependents — indicates financial burden.
is_high_bmi	Binary flag — 1 if BMI category is "Obese" or "Overweight".
is_smoker	Binary flag — 1 if smoking status is "Smoker".
region_encoded	Numerical encoding of region for distance-based models.
insurance_plan_encoded	Encoded values for insurance plan types.

Missing Value Treatment:

Verified dataset completeness and applied imputation strategies (if necessary).

Feature Scaling:

Normalized continuous features where required to enhance model performance.



---

## 🤖 Models Tried

- Linear Regression
- Ridge Regression
- XGBoost Regressor (Final Model)

### ✅ Final Model: XGBoost Regressor
With tuned hyperparameters:

```python
model = XGBRegressor(
    colsample_bytree=0.9,
    gamma=0.2,
    learning_rate=0.07,
    max_depth=4,
    n_estimators=150,
    subsample=0.8,
    random_state=42
)
```

---

## 📈 Results

The final model (XGBoost) outperformed others on training and test data, capturing complex nonlinear relationships in premium prediction.

---

## 🌐 Streamlit App

Try the app here:  
🔗 **[Health Premium Predictor Web App](https://health-premium-predictor-by-shiwan.streamlit.app)**

---

## 🖼️ App Screenshot

![Streamlit UI](https://github.com/shiwan-mangate/health-premium-predictor/blob/main/assets/app_screenshot.png)

---

## 🧠 Professional Use Case

This model can be deployed in:

- 🏥 Insurance company portals for real-time quote generation.
- 👥 Agent tools to advise clients.
- 📈 Financial analysis apps for premium estimations.

---

## 🚧 Future Improvements

- Improve accuracy with more diverse datasets.
- Add SHAP or LIME interpretability.
- Add REST API for wider deployment.

---

## 👨‍💻 Author

**Shiwan Mangate**  
B.Tech in Artificial Intelligence  
NIT Rourkela  
🔗 [GitHub](https://github.com/shiwan-mangate) | [LinkedIn](https://www.linkedin.com/in/shiwan-mangate-4568a9375)
