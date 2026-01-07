# 📊 Financial Risk & Profit Optimization Engine

## Overview

In commercial lending, **not all mistakes are equal**.

- A **loan default (False Negative)** costs a bank approximately **$150,000** in lost principal.
- A **rejected good loan (False Positive)** costs roughly **$15,000** in lost interest.

Most machine learning models optimize for **accuracy or AUC**, treating these errors equally.  
This project reframes the problem as a **profit maximization task**, building a financial risk decision engine that prioritizes **business outcomes over statistical precision**.

---

## Problem Statement

Traditional credit risk models use a fixed probability threshold (typically 0.50) and generic metrics such as accuracy.  
This ignores the **asymmetric financial impact** of incorrect decisions.

**Goal:**  
Maximize **net profit** while reducing exposure to costly defaults.

---

## Dataset

- **Source:** U.S. Small Business Administration (SBA) loan dataset
- **Size:** ~900,000 loans
- **Target Variable:**
  - `CHGOFF` → Default (1)
  - `P I F` → Paid in Full (0)
- **Observed Default Rate:** ~17.5%

---

## Key Innovations

### 1. Profit-Based Decision Optimization

- Defaults weighted **12× more costly** than rejected good loans
- Simulated P&L across probability thresholds
- Identified the **financially optimal threshold** instead of using 0.50

**Optimal Threshold:** `0.62`

**Impact:**  
~**$20M projected increase in net profit** on the test set compared to baseline decision logic.

---

### 2. Time-Series Validation (No Data Leakage)

To simulate real-world deployment:

- Data sorted by `DisbursementDate`
- First **80%** used for training (historical loans)
- Last **20%** used for testing (future loans)

This ensures the model never trains on future information — a critical requirement in fintech and risk modeling.

---

### 3. Ensemble Risk Modeling

- **Models Used:**
  - XGBoost
  - LightGBM
- **Technique:** Soft-voting ensemble
- **Imbalance Handling:** `scale_pos_weight`
- **Categorical Encoding:** Target Encoding

This approach improves stability and predictive robustness at scale.

---

### 4. Explainability & Regulatory Transparency

- Integrated **SHAP values**
- Provides loan-level explanations for every decision
- Enables clear, auditable reasoning behind loan rejections

Designed with **regulatory compliance and stakeholder transparency** in mind.

---

## Project Structure

```text
financial-risk-profit-engine/
│
├── images/                     # SHAP plots and profit visualizations
├── models/                     # Saved trained models
├── financial_risk_profit_engine.ipynb
├── requirements.txt
└── README.md
```

---

## Tech Stack

- Python
- Pandas / NumPy
- XGBoost
- LightGBM
- Scikit-learn
- SHAP
- Category Encoders
- Matplotlib / Seaborn

---

## Results Summary

| Metric | Baseline | Optimized |
|------|---------|-----------|
| Decision Threshold | 0.50 | **0.62** |
| Default Exposure | Higher | **Significantly Reduced** |
| Net Profit | Baseline | **+ $20M** |
| Explainability | ❌ | ✅ |

---

## Development Methodology

- Independently researched SBA lending patterns
- Designed profit-maximization logic from first principles
- Implemented the full modeling pipeline in Python
- Used AI tools **after core logic was complete** to:
  - Refactor for modularity
  - Improve readability
  - Optimize runtime performance

This mirrors real-world ML workflows where **human-led design is enhanced by modern tooling**.

---

## Future Improvements

- Explicit profit-based custom loss function
- Model monitoring and drift detection
- Stress testing across economic cycles
- Deployment-ready API layer (FastAPI)

---

## Author

**SB0904**  
Financial Risk Modeling | Applied Machine Learning | Profit Optimization
