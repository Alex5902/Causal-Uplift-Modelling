# Causal Uplift Modeling: From Simulation to Real-World Applications

This project demonstrates end-to-end **uplift modeling**, showcasing how machine learning can estimate the **incremental impact** of an intervention. Unlike traditional prediction tasks, uplift modeling predicts **who benefits because they received treatment**, enabling more effective targeting strategies.

---

## Project Overview

The work is structured into **three main notebooks**:

1. **[01_simulate_data.ipynb](notebooks/01_simulate_data.ipynb)**  
   *Simulate a synthetic educational dataset with known treatment effects.*  
   - Generate realistic dependencies between motivation, GPA, engagement, and study hours.
   - Assign treatment (private tuition) probabilistically, based on confounding variables.
   - Simulate counterfactual outcomes (`y0`, `y1`) and compute the true Individual Treatment Effect (ITE).

2. **[02_model_synthetic.ipynb](notebooks/02_model_synthetic.ipynb)**  
   *Train uplift models on synthetic data where true effects are known.*  
   - T-Learner, X-Learner, Causal Forest (CATE estimation).
   - Evaluate using:
     - Mean Squared Error (MSE) on ITE.
     - Qini curves and AUC.
     - Bayesian bootstrap intervals for model robustness.
   - Perform segment-level analysis to understand heterogeneity across GPA, engagement, and study hours.

3. **[03_model_criteo.ipynb](notebooks/03_model_criteo.ipynb)**  
   *Apply the same modeling pipeline to the real-world Criteo Uplift Dataset.*  
   - Train T-Learner, X-Learner, Causal Forest models.
   - Evaluate models using Qini AUC and credible intervals.
   - Use SHAP values to interpret drivers of conversion under treatment.
   - Simulate targeting strategies and estimate incremental revenue.

---

## Key Concepts

- **Uplift Modeling:** Predict the incremental impact of treatment vs. control.
- **Individual Treatment Effect (ITE):** $( y_1 - y_0 )$ per individual.
- **Meta-Learners:** T-Learner and X-Learner architectures for estimating uplift.
- **Causal Forest:** Nonparametric ensemble method to model heterogeneous treatment effects.
- **Qini Curve / AUC:** Evaluate how well the model ranks individuals by uplift.
- **SHAP Explainability:** Feature attribution for treatment response prediction.

---

## Why This Project Matters

This work illustrates:

- **Statistical Rigor:** Simulated data with known ground truth to validate models.
- **Business Relevance:** Real-world advertising dataset with practical recommendations.
- **Transparency:** Visualisations and credible intervals to quantify uncertainty.
- **Actionable Insights:** Segment uplift analysis and targeting simulations to inform strategy.

---

## Results Summary

### Synthetic Data
- **Best Model:** T-Learner for interpretability, Causal Forest for pure ITE accuracy.
- **MSE Reduction:** ~40% improvement over baseline.
- **Segment Analysis:** Higher uplift among engaged students with higher GPA and more study hours.

### Criteo Data
- **Best Model:** X-Learner achieved highest Qini AUC.
- **Top 10% Targeting:** Estimated +8-9% incremental conversions.
- **Revenue Impact:** Simulated £10,000-£14,000 uplift per campaign.

---

## Repository Structure
```
data/
    ├── synthetic_education_uplift.csv
    └── criteo-research-uplift-v2.1.csv
notebooks/
    ├── 01_simulate_data.ipynb
    ├── 02_model_synthetic.ipynb
    └── 03_model_criteo.ipynb
README.md
```
---

## How to Reproduce

1. Clone the repository:
https://github.com/Alex5902/Causal-Uplift-Modelling.git
cd Causal-Uplift-Modelling

2. Install dependencies:
pip install -r requirements.txt

3. Run notebooks in order:
- `01_simulate_data.ipynb`
- `02_model_synthetic.ipynb`
- `03_model_criteo.ipynb`