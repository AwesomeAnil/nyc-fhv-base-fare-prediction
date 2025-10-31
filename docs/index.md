![Banner](/predictions.png)

# 🚖 NYC FHV Base Fare Prediction  
*Predictive Analytics for Smart Urban Mobility*

![GitHub last commit](https://img.shields.io/github/last-commit/AwesomeAnil/nyc-fhv-base-fare-prediction)
![GitHub Repo stars](https://img.shields.io/github/stars/AwesomeAnil/nyc-fhv-base-fare-prediction?style=social)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Python](https://img.shields.io/badge/Python-3.11-blue.svg)
![Power BI](https://img.shields.io/badge/PowerBI-Dashboard-orange.svg)
![Microsoft Fabric](https://img.shields.io/badge/Microsoft-Fabric-blueviolet.svg)
![LightGBM](https://img.shields.io/badge/Model-LightGBM-yellow.svg)

---

## 🧭 Executive Summary  
> A data-driven framework to **forecast base fares** for NYC For-Hire Vehicles, combining Spark + Delta + ML pipelines and Power BI visualisation.  
> Enables dynamic pricing, profitability optimisation, and transparent governance for regulators and operators alike.

---

## 🎯 Business Motivation  
- Urban mobility pricing is volatile — small fare misalignments create huge financial impact.  
- Regulators demand traceable, explainable pricing models.  
- Data-science-driven fare governance creates competitive advantage and public trust.

**Strategic Impact:**  
- Smarter base-fare setting → improved margins  
- Regulatory confidence → audit-ready analytics  
- Enhanced driver & rider satisfaction → better utilisation  

---

## 🏗️ Solution Architecture  
1. **Data Ingestion** – NYC TLC trip data (~20 M records)  
2. **Feature Engineering** – 77 features (temporal, geospatial, behavioural)  
3. **Model Training** – XGBoost / LightGBM / CatBoost ensembles  
4. **Validation & Monitoring** – Explainable metrics, fairness & outlier detection  
5. **Visualisation & Governance** – Power BI dashboards for executive decisions  

---

## 📈 Model Performance Highlights  
| Model | R² | RMSE | MAE |
|-------|----|------|-----|
| Linear Regression | 0.74 | 0.33 | 0.25 |
| XGBoost | **0.869** | 0.24 | 0.17 |
| CatBoost | **0.870** | 0.24 | 0.17 |
| LightGBM | **0.871** | 0.238 | 0.173 |

*✅ Achieved up to 89 % accuracy predicting base-fare components.*

---

## 💡 Power BI Executive Dashboard  
> **Base fares training and prediction accuracy.**

[🔗 View Base Fare Prediction Report (New tab)](https://awesomeanil.github.io/nyc-fhv-base-fare-prediction/BaseFare.html)

<div align="center">
<!-- 👉 Replace below link with your actual Power BI embed link -->
<iframe width="100%" height="650px" src="https://app.powerbi.com/view?r=eyJrIjoiZmNkZWM4NzEtZDZkNy00OGY1LTlhN2MtNjY3NjMwMDA4NzRmIiwidCI6ImY2NTRlNzkxLWY4NTgtNDZkNi05MWE5LTE5YzlmZTA4YTc0ZiJ9" frameborder="0" allowFullScreen="true"></iframe>
</div>

---

## 🧩 Repository Overview  
| Folder | Description |
|:--|:--|
| `README.md` | High-level summary |
| `docs/| Docs for repo |
| `images/` | screenshots and visuals of charts |
| `notebooks/` | Data prep, EDA & model notebooks |
| `sample_data/` | samples of raw NYC TLC parquet data |
| `powerbi/` | PDF files of dashboards & reports |

---

## 🏆 Key Outcomes  
- **Optimised base-fare recommendations** across zones and time-buckets.  
- **Transparent governance framework** for pricing compliance.  
- **Enterprise-ready ML pipeline** – modular, auditable, and scalable.  
- **Operational uplift** through predictive insights integrated with Microsoft Fabric and Power BI.

---

## 🧱 Technology Stack  
| Layer | Tools |
|-------|-------|
| Data Processing | Apache Spark / Delta Lake |
| Modelling | LightGBM / XGBoost / CatBoost |
| Analytics | Python / Pandas / Scikit-Learn |
| BI Layer | Power BI / Microsoft Fabric |
| Deployment & Ops | GitHub / VS Code / Jupyter |

---

## 📚 Project Documentation

| 📄 Document | 🔍 Description |
|--------------|----------------|
| [🧠 **Analysis Flow**](analysis_flow.md) | End-to-end overview of the project pipeline — from data acquisition, engineering, and modeling, to visualization and insights delivery. |
| [⚙️ **Configuration Guide**](CONFIGURATION.md) | Detailed setup instructions for environment variables, file paths, and parameter tuning. Ideal for contributors or users running the pipeline locally or in Microsoft Fabric. |
| [💻 **Environment Setup**](ENVIRONMENT.md) | Step-by-step guide to setting up the Python, PySpark, and Fabric environments — including dependencies, versioning, and reproducibility practices. |
| [📈 **Executive 1-Pager**](EXEC_1PAGER.md) | Concise summary tailored for executives and stakeholders — highlights business objectives, outcomes, and key success metrics. |
| [🎯 **Presentation Deck**](PRESENTATION.md) | Visual storytelling of the project’s journey — data strategy, insights, model performance, and business impact designed for boardroom delivery. |


---

## 🙌 Credits  
**Author:** Anil Jacob  
**GitHub:** [github.com/AwesomeAnil/nyc-fhv-base-fare-prediction](https://github.com/AwesomeAnil/nyc-fhv-base-fare-prediction)  
**LinkedIn:** [linkedin.com/in/anil-jacob](https://www.linkedin.com/in/anil-jacob)  

Special thanks to:  
- **NYC TLC** – Public FHV Trip Data  
- **Microsoft Fabric / Power BI Community** – Analytics enablement  
- **Open-source contributors** – LightGBM, XGBoost, CatBoost

---

> © 2025 Anil Jacob · All rights reserved.
