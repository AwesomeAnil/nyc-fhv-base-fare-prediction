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

* Derived binary flags: `airport_flag`, `shared_match`, `access_a_ride`.
* Log transformations to normalize skewed variables (trip time, tips).
* Standard scaling applied to all numeric features.

**Box-plots of features (log-transformed + standard scaling)** 

![Boxplots of transformed vraiables](/images/Boxplot_log_transformed_standard_scaler.png)

---

## 🤖 Modeling

**Algorithm Used:** Linear Regression (Statsmodels OLS)

**Model Summary:** 

![LR Results from Statsmodel](/images/LR_Results.png)

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
