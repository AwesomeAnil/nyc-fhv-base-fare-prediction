# 🚖 NYC FHV Base Fare Prediction

---

# Table of Contents

1. 🎯 Objective
2. 🚖 NYC FHV Base Fare Prediction
3. 🎯 Business Problem
4. 📂 Dataset
5. 📊 Data & EDA Overview
6. 🔍 Univariate Analysis (Base Passenger Fares)
7. 🔗 Bivariate Analysis (Examples)
8. 🛠 Feature Engineering
9. 🤖 Baseline Model
10. 🏆 Model Selection — Advanced Models
11. 🌳 Best Model — LightGBM
12. 🔮 Predictions on New Data
13. 💼 Business Impact
14. 📊 Workflow Summary
15. ✅ Takeaways
16. 📌 Next Steps
17. ⚡ End of Presentation ⚡

---
## 🎯 Objective

- Predict base passenger fares for NYC High-Volume For Hire Vehicle (FHV) services
- Build an end-to-end ML pipeline on Microsoft Fabric
- Support regulators, operators, and riders with transparent, data-driven insights

---

## 🎯 Business Problem

NYC High-Volume For Hire (FHV) operators and regulators face several challenges:

* **Pricing Transparency**: Ensuring riders are charged fair, consistent fares.
* **Revenue Forecasting**: Estimating base fare revenues for financial planning.
* **Regulatory Compliance**: Supporting NYC TLC reporting obligations.
* **Fraud Detection**: Identifying anomalous trips with inflated or under-reported fares.
* **Operational Strategy**: Segmenting trips (airport vs. city, shared vs. solo) to optimize allocation and profitability.

**Goal:** Build a **predictive model** for base fares that delivers accurate, explainable insights.

---

## 📂 Dataset

- Training data: ~2M trips from June 2025
- Prediction data: ~20M unseen trips from July 2025
- Features:
   - Trip miles, trip time
   - Surcharges, tolls, tips
   - Driver pay
   - Flags: airport, shared rides, WAV, Access-a-Ride
   - Temporal markers: hour-of-day, weekday/weekend

---

## 📊 Data & EDA Overview

**Source**: NYC TLC High-Volume FHV Trip Records.
**Features analyzed**:

* base_passenger_fare
   - Mean: $27.55
   - Median: $19.99
   - Min/Max: $6.19 – $129.90
   - Std Dev: 22.73
   - IQR: 12.67 – 33.57
   - Fare distribution is right-skewed with many low-to-mid fares and some high fares inflating the mean. Typical fares are between $12–$34
* driver_pay_per_mile
   - Mean: 5.54
   - Median: 4.91
   - Min/Max: 2.44 – 18.30
   - Std Dev: 2.69
   - IQR: 3.84 – 6.30
   - Most trips have driver pay around $4–$6 per mile. Some trips have extremely high pay rates (up to 18.3), creating right-skewness.
* trip_miles
   - Mean: 5.00 miles
   - Median: 3.03 miles
   - Min/Max: 0.48 – 27.69 miles
   - Std Dev: 5.20
   - IQR: 1.56 – 6.42 miles
   - Most trips are short to moderate distance. The median is lower than the mean, indicating a right-skewed distribution with some long trips (up to 27.69 miles) driving the mean upward.
* Trip time:
  - Mean: 1209.28 minutes (~20 hours – seems unusually high; likely units issue or aggregated trips)
  - Median: 978 minutes (~16 hours)
  - Min/Max: 194 – 4459 minutes (~3 hours to 74 hours)
  - Std Dev: 846.95
  - IQR: 600 – 1566 minutes
  - There is very high variability in trip times. Right-skewed with extreme maximum values. Most trips are under 26 hours (75th percentile). There may be outliers or data entry issues, given unusually long times.
 * Tolls:
   - Mean: 1.07
   - Median: 0.00
   - Min/Max: 0.00 – 18.52
   - Std Dev: 3.34
   - IQR: 0.00 – 0.00
   - Most trips do not include tolls (median = 0), but some trips incur very high tolls, creating a heavily right-skewed distribution.
 * Congestion surcharge:
   - Mean: 0.97
   - Median: 0.00
   - Min/Max: 0.00 – 2.75
   - Std Dev: 1.31
   - IQR: 0.00 – 2.75
   - Many trips do not incur congestion charges (median = 0), but some trips have high surcharges, indicating right-skew.
 * Airport fee:
   - Mean: 0.22
   - median: 0.00
   - Min/Max: 0.00 – 2.50
   - Std Dev: 0.71
   - IQR: 0.00 – 0.00
   - Most trips do not include airport fees, but a few trips have substantial fees. Highly right-skewed.
 * Tips:
   - Mean: 1.16
   - Median: 0.00
   - Min/Max: 0.00 – 18.03
   - Std Dev: 3.11
   - IQR: 0.00 – 0.00
   - Most passengers do not tip, but the tip distribution has a long right tail with some high tipping trips.

---

## 🔍 Univariate Analysis (Base Passenger Fares)

* **Trip Time**: Right-skewed distribution; capped extreme outliers.
* **Tips**: Long-tail distribution; majority trips with minimal tips, few with very high.
* **Tolls & Surcharges**: Step-like distributions reflecting NYC pricing rules.
* **Driver Pay**: Concentrated around specific bands; indicative of standardized trip categories.

**Base Fares Distribution** 

![EDA Base fares Distribution](/images/EDA_base_fares_plot.png)

**Driver Pay Distribution**

![EDA Driver Pay Distribution](/images/EDA_Driver_Pay.png)

---

## 🔗 Bivariate Analysis (Examples)

* **Trip Time vs. Base Fare**: Positive correlation; non-linear at higher durations.
* **Airport Trips vs. Base Fare**: Airport flag strongly associated with higher base fare.
* **Congestion Surcharge vs. Fare**: Distinct fare lift observed with surcharge applied.
* **Shared Ride vs. Fare**: Shared-match flag linked to slightly reduced fares.

*(Insert links to scatterplots & grouped bar plots: `img/bivariate_triptime_fare.jpeg`, `img/bivariate_airport_fare.jpeg`, etc.)*

**Scatter plots** 

![EDA Scatter plots](/images/EDA_Scatter_plots.png)

**Bivariate Plots** 

![EDA Bivariate Plots](/images/EDA_bivariate_plots.png)

---

## 🛠 Feature Engineering

* Built 77 predictors
* Transformations: log-normalization, scaling
* Derived binary flags: `airport_flag`, `shared_match`, `access_a_ride`.
* Temporal features: peak hours, weekends, weekdays
* Log transformations to normalize skewed variables (trip time, tips).
* Standard scaling applied to all numeric features.

**Box-plots of features (log-transformed + standard scaling)** 

![Boxplots of transformed vraiables](/images/Boxplot_log_transformed_standard_scaler.png)

---

## 🤖 Baseline Model

**Algorithm Used:** Linear Regression (Statsmodels OLS)

**Model Summary:** 

![LR Results from Statsmodel](/images/LR_Results.png)

**Model Fit:**

* **R² = 0.74** → Explains **74% of variance** in base passenger fares, **RMSE = 0.33, MAE = 0.25**.
* **F-statistic = 3.31e+06, p < 0.001** → Model highly significant.
* **Durbin-Watson ≈ 2.00** → Residuals show no autocorrelation.
* **Sample size (N = 1,600,000)** → Results are robust and generalizable.

---

## 🏆 Model Selection — Advanced Models

Candidate models:
- Linear Regression (baseline)
- XGBoost
- CatBoost
- LightGBM
- Neural Nets (MLPs with PyTorch)

**Leaderboard Results**:
| Model                        | R²        | RMSE     | MAE      |
| ---------------------------- | --------- | -------- | -------- |
| Linear Regression (baseline) | 0.740     | 0.33     | 0.25     |
| XGBoost                      | 0.869     | 0.24     | 0.17     |
| CatBoost                     | 0.870     | 0.24     | 0.17     |
| Neural Net (basic MLP)       | 0.862     | 0.24     | 0.18     |
| Neural Net (stronger MLP)    | 0.867     | 0.238    | 0.173    |
| **LightGBM (best)**          | **0.888** | **0.22** | **0.16** |

---

## 🌳 Best Model — LightGBM

- **Accuracy**: R² = 0.888, RMSE = 0.22, MAE = 0.16
- **Feature importance**:
   - Base calculated fare
   - Trip miles & trip time
   - Driver pay
   - Airport flag, surcharges

#### 📈 Feature Importance Plot

![Feature Importance Plot](/images/Feature_Importance.png)

## 🔮 Predictions on New Data

- Applied LightGBM to 20M unseen July 2025 trips
- Accuracy held strong (R² ≈ 0.87, RMSE ≈ 0.23, MAE ≈ 0.17)
- Predictions integrated into Power BI dashboards for:
   - Real-time monitoring
   - Scenario analysis (e.g., surcharge changes)
   - Outlier / fraud detection

#### 📈 Predicted vs Actual fares

![Predicted vs. Actual Fares](/images/predicted_vs_actuals.png)

#### 📊 Power BI Report

![Power BI report](/images/power_bi_report_predictions.png)
---

## 💼 Business Impact

* **Revenue Forecasting**: Accurate monthly projections at scale
* **Pricing Strategy**: Data-driven surcharge & airport fee evaluation
* **Regulatory Transparency**: Baseline model provides interpretability
* **Fraud Prevention**: Outlier detection flags anomalies

---

## 📊 Workflow Summary

#### flowchart LR

![Workflow Summary](/images/Workflow_Summary.png)

---

## ✅ Takeaways

* Built an **end-to-end ML pipeline** in Microsoft Fabric.
* Delivered a **highly accurate, interpretable regression model** for fare predictions.
* **Univariate & Bivariate analysis** provide stakeholder confidence in model insights.
* Foundation is set for **advanced ML models (Random Forest, XGBoost, Neural Nets)** in future iterations.

---

## 📌 Next Steps

- Extend to **fare + tip prediction**
- Explore **ensemble models** for added robustness
- Deploy as **API services** for real-time scoring
- Expand scope to **regulatory monitoring and compliance dashboards**

---

⚡ *End of Presentation* ⚡
