![Banner](predictions.png)

# 🚖 NYC FHV Base Fare Prediction — Executive 1-Pager

## 🎯 Objective

Predict NYC High-Volume For Hire Vehicle (FHV) **base fares** using machine learning to deliver:

* **Fair pricing & transparency**
* **Revenue forecasting**
* **Regulatory compliance**
* **Fraud detection**

---

## 📂 Data at Scale

* **Training**: ~2M trips from **June 2025**
* **Predictions**: ~20M trips from **July 2025** (unseen data)
* **Key features**:

  * Trip miles & trip time
  * Surcharges, tolls, tips
  * Driver pay
  * Temporal patterns (hour, weekday, weekend)
  * Special flags (airport, shared, WAV, AAR)

---

## 🔎 Key Results

* **Baseline model (Linear Regression)**: 74% accuracy (R² = 0.74)
* **Best model (LightGBM)**: 89% accuracy (R² = 0.888)
* **Unseen data test (20M July trips)**: 87% accuracy (R² ≈ 0.87)

#### 📊 *Model Leaderboard*

![Model Training Leaderboards](/images/leaderboards.png)

#### 📈 *Predicted vs Actuals*

![Predicted vs. Actuals](/images/predicted_vs_actuals.png)

#### 📈 *Power BI Report*

![Power BI report](/images/power_bi_report_predictions.png)

---

## 💼 Business Value

* **Revenue Forecasting** → Predicts fares for 20M+ trips per month at scale
* **Pricing Strategy** → Evidence-based evaluation of surcharges & airport trips
* **Transparency** → Baseline regression offers simple, regulator-friendly interpretability
* **Fraud Detection** → Outlier predictions highlight anomalies in real time

---

## 🚀 Takeaway

A **production-ready ML pipeline** built on Microsoft Fabric demonstrates:

* High predictive accuracy (≈89%)
* Scalability to industry volume (20M trips/month)
* Actionable insights for regulators, operators, and riders

📊 *Pipeline diagram*

![ML Pipeline](/images/pipeline.png)

---

✅ This file is concise, business-facing, and ideal for:

* Leadership briefings
* Non-technical stakeholders
* Policy and regulatory presentations

---
