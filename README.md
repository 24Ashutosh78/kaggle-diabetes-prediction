# kaggle-diabetes-prediction
# Kaggle Diabetes Prediction (Playground Series)

End-to-end machine learning pipeline for diabetes risk prediction using
advanced medical feature engineering, regularized tree ensembles, and
probability calibration. Achieved **Top 15% leaderboard** performance.

## 🏆 Key Results
- Public Leaderboard AUC: **0.721+**
- Cross-validation AUC: **0.724**
- Kaggle Rank: **Top 15%**
- Best single model: LightGBM (CV AUC: 0.7268)


## 🏗️ Pipeline Overview

Raw Data (27 features)  
→ 30+ engineered medical & lifestyle features  
→ [CatBoost | XGBoost | LightGBM] (5-fold CV)  
→ Regularized ensemble (equal weights)  
→ Mean-shift probability calibration  
→ Final submission (AUC 0.721+)

## 🧪 Modeling Evolution

**Phase 1 – Baseline**
- CatBoost (5-fold CV)
- CV AUC: 0.7238
- Limitation: minimal feature engineering

**Phase 2 – Medical Feature Engineering**
- Lipid ratios (LDL/HDL, TG/HDL)
- Blood pressure metrics
- Lifestyle risk score
- CV ↑ to 0.7272, but LB drop → overfitting detected

**Phase 3 – Overfit Ensemble**
- 15-model ensemble (multiple seeds)
- Large CV–LB gap (−0.03)
- OOF mean ≈ 0.63 (expected ≈ 0.15) → severe miscalibration

**Phase 4 – Regularized Ensemble (Final)**
- Reduced depth & model count
- Strong regularization
- CV: 0.724 → LB: 0.721+

**Phase 5 – Probability Calibration**
- Mean-shift calibration using train prevalence
- Stable probabilities & leaderboard consistency

## 🔧 Key Innovations

### Medical Domain Features
- Pulse pressure (vascular risk)
- LDL/HDL ratio (metabolic syndrome marker)
- Lifestyle risk score (sleep, activity, screen time)
- Comorbidity count

### Overfitting Diagnosis
- CV–LB gap analysis
- OOF mean sanity checks

### Production-Ready Calibration
- Mean-shift probability calibration
- Preserves ranking while fixing prevalence bias