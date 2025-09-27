# 🚖 NYC FHV Base Fare Prediction

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

## 📊 Data & EDA Overview

* **Source**: NYC TLC High-Volume FHV Trip Records.
* **Features analyzed**:

  * Trip time
  * Tolls
  * Congestion surcharge
  * Airport fee
  * Tips
  * Flags (shared ride, airport, access-a-ride)

---

## 🔍 Univariate Analysis (Examples)

* **Trip Time**: Right-skewed distribution; capped extreme outliers.
* **Tips**: Long-tail distribution; majority trips with minimal tips, few with very high.
* **Tolls & Surcharges**: Step-like distributions reflecting NYC pricing rules.
* **Driver Pay**: Concentrated around specific bands; indicative of standardized trip categories.

*(Insert links to histograms & boxplots: `img/univariate_trip_time.jpeg`, `img/univariate_tips.jpeg`, etc.)*

---

## 🔗 Bivariate Analysis (Examples)

* **Trip Time vs. Base Fare**: Positive correlation; non-linear at higher durations.
* **Airport Trips vs. Base Fare**: Airport flag strongly associated with higher base fare.
* **Congestion Surcharge vs. Fare**: Distinct fare lift observed with surcharge applied.
* **Shared Ride vs. Fare**: Shared-match flag linked to slightly reduced fares.

*(Insert links to scatterplots & grouped bar plots: `img/bivariate_triptime_fare.jpeg`, `img/bivariate_airport_fare.jpeg`, etc.)*

---

## 🛠 Feature Engineering

* Derived binary flags: `airport_flag`, `shared_match`, `access_a_ride`.
* Log transformations to normalize skewed variables (trip time, tips).
* Standard scaling applied to all numeric features.
* Interaction terms (e.g., `trip_time × congestion_surcharge`).

---

## 🤖 Modeling

**Algorithm Used:** Linear Regression (Statsmodels OLS)

**Model Fit:**

* **R² = 0.954** → Explains **95.4% of variance** in base passenger fares.
* **F-statistic = 3.31e+06, p < 0.001** → Model highly significant.
* **Durbin-Watson ≈ 2.00** → Residuals show no autocorrelation.
* **Sample size (N = 1,600,000)** → Results are robust and generalizable.

---

### 📊 Feature Impact (Standardized Coefficients)

> *Note: Features were **log-transformed and standardized** before modeling. Coefficients indicate **relative influence**, not absolute fare impact in dollars.*

| Feature                  | Relative Effect | Interpretation                                                               |
| ------------------------ | --------------- | ---------------------------------------------------------------------------- |
| **bcf**                  | +0.430          | Strongest positive influence on fares                                        |
| **driver_pay**           | +0.264          | High driver pay correlates with higher fares                                 |
| **time_of_day_Night**    | +0.022          | Night trips increase fares relative to other times                           |
| **time_of_day_Morning**  | +0.014          | Morning trips have moderate positive effect                                  |
| **time_of_day_Evening**  | +0.011          | Evening trips slightly increase fares                                        |
| **access_a_ride_flag_1** | +0.011          | Small positive effect for accessibility trips                                |
| **shared_match_flag_1**  | -0.003          | Shared rides slightly reduce fares                                           |
| **is_weekend_1**         | -0.006          | Weekend trips slightly reduce fares                                          |
| **wav_match_flag_1**     | -0.048          | WAV trips reduce fares relative to standard trips                            |
| **trip_miles**           | -0.045          | Longer trips slightly reduce fares (after scaling/log-transform adjustments) |

*(Insert standardized coefficient bar chart: `img/feature_importance.jpeg` — color-coded by positive vs negative effect)*

---

## 🔮 Predictions on New Data

* Applied trained regression model to unseen FHV trip records.
* Generated predicted fares alongside actuals.
* Validation plots show **tight alignment**, proving model generalization.

*(Insert prediction vs. actuals scatterplot: `img/predicted_vs_actual.jpeg`)*

---

## 💼 Business Impact

* **Revenue Forecasting:** Predictable cashflows for operators.
* **Pricing Strategy:** Evidence for congestion surcharge / airport pricing debates.
* **Regulatory Reporting:** Transparent model for TLC compliance.
* **Fraud Detection:** Highlight outliers where fares deviate significantly from predicted.

---

## ✅ Takeaways

* Built an **end-to-end ML pipeline** in Microsoft Fabric.
* Delivered a **highly accurate, interpretable regression model** for fare predictions.
* **Univariate & Bivariate analysis** provide stakeholder confidence in model insights.
* Foundation is set for **advanced ML models (Random Forest, XGBoost, Neural Nets)** in future iterations.

---

## 📌 Next Steps

* Deploy prediction pipeline on **Fabric Lakehouse**.
* Integrate with **Power BI dashboards** for real-time monitoring.
* Expand scope with **advanced ML algorithms** for higher accuracy.

---

⚡ *End of Presentation* ⚡
