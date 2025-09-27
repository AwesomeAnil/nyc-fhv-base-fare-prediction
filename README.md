# 🚖 NYC For-Hire Vehicle Base Fare Prediction

> **Portfolio Project**: Combining advanced machine learning with stakeholder-focused insights to predict and optimize NYC For-Hire Vehicle (FHV) base fares.

---

## 🌟 Project Highlights
- **End-to-End ML Pipeline**: Data ingestion → feature engineering → model training → prediction.  
- **Stakeholder Value**: Enables operators to forecast base fares, optimize pricing, and assess revenue opportunities.  
- **Scalable on Microsoft Fabric**: Built natively on Fabric’s **Lakehouse + Spark + Delta** ecosystem for reproducibility.  
- **Interdisciplinary**: Bridges *statistical rigor* and *business impact*.  

---

## 📂 Repository Structure
- `notebooks/` – Analysis and ML workflow  
- `reports/` – Executive & technical summaries for stakeholders  
- `results/` – Metrics, visualizations, prediction outputs  
- `docs/` – Architecture, methodology, governance considerations  

---

## 🚀 Workflow
1. **EDA & Feature Engineering**  
   - Explored ride patterns (airport trips, tolls, tips, congestion surcharge).  
   - Engineered new features to capture demand & cost drivers.  

2. **Model Training & Evaluation**  
   - Built regression & ensemble models.  
   - Benchmarked with **R²**, **RMSE**, and **MAE**.  

3. **Predictions on New Data**  
   - Applied trained model to unseen ride records.  
   - Produced predicted base fares with confidence intervals.  

---

## 📊 Results (Technical)
- Best-performing model: **[insert model name here]**  
- Achieved **R² = X.XX**, **RMSE = Y.YY**, **MAE = Z.ZZ**.  
- Outperformed baseline regression benchmarks.  

---

## 💼 Business Impact (Stakeholder Lens)
- **Revenue Forecasting**: Provides operators foresight into trip-level base fare revenues.  
- **Pricing Strategy**: Identifies sensitivity to congestion charges, tolls, and ride flags.  
- **Operational Planning**: Helps in segmenting trips (airport vs. city) for optimized allocation.  
- **Decision Enablement**: Demonstrates how AI/ML insights can be embedded into financial planning.  

---

## 🛠 Tech Stack
- **Microsoft Fabric**: Lakehouse, Spark, Delta tables, ML notebooks  
- **Python**: pandas, scikit-learn, matplotlib, seaborn  
- **ML Principles**: Feature engineering, model validation, prediction pipeline  

---

## 📈 Visuals
*(include a few charts / screenshots from notebooks here)*  
- Feature importance plot  
- Model performance comparison  
- Prediction vs. actual fares  

---

## 📌 Getting Started
```bash
git clone https://github.com/<your-username>/nyc-fhv-base-fare-prediction.git
cd nyc-fhv-base-fare-prediction
pip install -r requirements.txt
jupyter lab
```

---

## 📄 License
This project is licensed under the [MIT License](LICENSE).  
