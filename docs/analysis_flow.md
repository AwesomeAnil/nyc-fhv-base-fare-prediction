# 🧭 Data Science Workflow — NYC FHV Base Fare Prediction

> *A transparent look into the full lifecycle — from raw parquet data to an executive-ready Power BI experience.*

---

## 🚀 1. Data Acquisition

**Source:**  
NYC TLC High-volume For-Hire Vehicle (FHV) Parquet datasets  
📦 Over 15 million trip records sourced directly from [NYC Taxi & Limousine Commission (TLC)](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

**Actions:**  
- Downloaded raw `.parquet` trip datasets (2019–2024).  
- Validated schema consistency across months.  
- Consolidated into a unified base dataset for engineering.

---

## ⚙️ 2. Data Engineering in Microsoft Fabric

**Platform:** Microsoft Fabric (Lakehouse + PySpark)  

**Highlights:**  
- Mounted parquet data into Fabric Lakehouse.  
- Cleaned missing and inconsistent records.  
- Enforced schema typing (timestamps, floats, categoricals).  
- Derived engineered features such as `trip_duration`, `distance_bucket`, and `time_of_day_band`.

🧱 *Output:* Clean, version-controlled Delta tables ready for modeling.

---

## 🧪 3. Feature Engineering & EDA

**Environment:** PySpark Notebooks  

**Analytical Focus:**  
- Outlier detection (Z-score & IQR)  
- Correlation analysis between predictors  
- Feature importance ranking (via LightGBM feature importances)  
- Handling skewness and log-transformations  

📊 *EDA deliverables:*  
- Distribution plots  
- Correlation heatmaps  
- Outlier & residual visualizations  

---

## 🤖 4. Model Training & Optimization

**Algorithms Used:**  
- Linear Regression (Baseline)  
- LightGBM Regressor (Optimized Model)

**Approach:**  
- Train-test split (80/20)  
- Hyperparameter tuning via grid search  
- Cross-validation for generalization performance  

📈 *Key Metrics:*  
- RMSE  
- R² Score  
- MAE  
- Residual plots for bias/variance analysis  

---

## 🧮 5. Model Evaluation & Selection

**Model Comparison:**  
| Model | RMSE | R² | Notes |
|:------|-----:|----:|------|
| Linear Regression | 3.45 | 0.82 | Stable baseline |
| LightGBM | **2.71** | **0.91** | Best performer |

🏆 *Selected Model:* LightGBM (optimal trade-off between speed & accuracy)

---

## 📊 6. Power BI Visualization & Semantic Modeling

**Purpose:**  
To bring predictive insights to non-technical stakeholders via an interactive executive dashboard.

**Actions:**  
- Imported predictions and summary statistics into Power BI.  
- Built DAX-based semantic models for quick slice-and-dice.  
- Designed clean, high-impact visuals with a focus on fare trends and prediction accuracy.  

🎯 *Result:* A fully interactive **Executive Power BI Dashboard** for decision-makers.  

👉 [View the Live Power BI Report](https://app.powerbi.com/view?r=eyJrIjoiZmNkZWM4NzEtZDZkNy00OGY1LTlhN2MtNjY3NjMwMDA4NzRmIiwidCI6ImY2NTRlNzkxLWY4NTgtNDZkNi05MWE5LTE5YzlmZTA4YTc0ZiJ9)

---

## 🪄 7. Workflow Visualization

> *Each stage contributes to a seamless pipeline — from raw data to polished insights.*

<div align="center">
  <img src="docs/workflow.png" alt="Data Science Workflow" width="25%">
</div>

---

## 🙌 Credits

**Project Author:** [Anil Jacob](https://www.linkedin.com/in/aniljacob-data)  
**Repository:** [github.com/AwesomeAnil/nyc-fhv-base-fare-prediction](https://github.com/AwesomeAnil/nyc-fhv-base-fare-prediction)  

---

> _Crafted with precision using Microsoft Fabric, PySpark, and Power BI._  
> *Data-driven design for real-world impact.*

