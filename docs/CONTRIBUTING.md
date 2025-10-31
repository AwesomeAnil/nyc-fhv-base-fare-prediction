# 🤝 Contributing to NYC FHV Base Fare Prediction

> Thank you for your interest in contributing!  
> This repository represents a complete, end-to-end **data science and BI engineering workflow** — from raw NYC FHV parquet datasets to an enterprise-ready Power BI experience.

We welcome meaningful contributions that strengthen **data quality**, **model robustness**, **reproducibility**, or **visual storytelling**.  
Whether you’re improving PySpark transformations, refining LightGBM parameters, or enhancing documentation — your contribution is valued.

---

## 🧭 Guiding Principles

1. **Data Integrity First**  
   All data transformations must preserve logical and statistical consistency.  

2. **Clarity Over Cleverness**  
   Write code that others can read and extend — even under time pressure.  

3. **Reproducibility**  
   Any contributor should be able to reproduce your results using the documented environment.  

4. **Transparency**  
   Document every major decision in commits, PR descriptions, or markdown notes.

---

## 🧑‍💻 Getting Started

### Prerequisites
- Python ≥ 3.10  
- PySpark, Pandas, LightGBM, and supporting ML libraries  
- Microsoft Fabric or equivalent Lakehouse environment  
- Power BI Desktop (for visualization & semantic modeling)

### Local Setup
```bash
# 1️⃣ Fork this repository
# 2️⃣ Clone your fork
git clone https://github.com/<your-username>/nyc-fhv-base-fare-prediction.git

# 3️⃣ Create a feature branch
git checkout -b feature/your-feature-name

# 4️⃣ Install dependencies
pip install -r requirements.txt

# 5️⃣ Launch Jupyter or your preferred notebook environment
jupyter notebook
```
---

## 🧩 Areas You Can Contribute

| Category | Description |
|-----------|--------------|
| 📦 **Data Engineering** | Improve or validate PySpark transformations and Delta Lake schema handling. |
| 🧠 **Modeling & ML** | Experiment with new regression models, hyperparameter tuning, or feature engineering. |
| 📊 **Visualization** | Enhance Power BI visuals, DAX measures, or executive storytelling. |
| 📜 **Documentation** | Improve explanations, visuals, and markdown clarity for non-technical readers. |
| 🧱 **Infrastructure** | Propose scalable improvements for deployment or Fabric workspace configuration. |

---

## 🧮 Pull Request Guidelines

- Keep PRs focused and descriptive.  
- Include a short summary of your changes in the PR body.  
- If applicable, add screenshots or sample outputs.  
- Ensure all notebooks run cleanly from top to bottom without manual intervention.  

---

## 🧰 Coding Standards

- Follow **PEP8** for Python style.  
- Use **snake_case** for variables and **PascalCase** for classes.  
- Avoid hard-coded file paths — prefer environment variables or config files.  
- Add inline comments to clarify complex logic.  

---

## 🧪 Testing & Validation

Before submitting a PR:  
1. Run all transformation and modeling notebooks end-to-end.  
2. Validate that model evaluation metrics (RMSE, R²) remain within expected thresholds.  
3. Ensure Power BI outputs are unaffected or improved.  

---

## 🌐 Communication

Have questions or suggestions?  
- Start a [GitHub Discussion](https://github.com/AwesomeAnil/nyc-fhv-base-fare-prediction/discussions)  
- Open an [Issue](https://github.com/AwesomeAnil/nyc-fhv-base-fare-prediction/issues/new)  
- Connect with **[@AwesomeAnil](https://github.com/AwesomeAnil)** on GitHub  
- Or reach out on [LinkedIn](https://www.linkedin.com/in/aniljacob-data)  

---

## 🙌 Acknowledgements

This repository integrates:  
- **Microsoft Fabric** for unified lakehouse analytics  
- **PySpark + Delta Lake** for data engineering  
- **LightGBM** for predictive modeling  
- **Power BI** for executive-level data storytelling  

> Each contribution helps evolve this project toward a world-class **data analytics blueprint** for large-scale predictive modeling.

---

*Curated and maintained by [Anil Jacob](https://www.linkedin.com/in/aniljacob-data)*  
⭐ If you found this repository valuable, consider starring it to show your support.





