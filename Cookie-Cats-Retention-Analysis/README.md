# Cookie Cats Retention Analysis

This project analyzes player retention in the mobile puzzle game **Cookie Cats** through A/B testing and predictive modeling. The goal is to evaluate how changing the progression gate from level 30 to 40 impacts retention, and to predict which users are likely to return after 1 or 7 days.

Built for portfolio demonstration and aligned with real-world product analytics expectations.

---

## 📌 Objectives

- **A/B Testing**: Assess whether moving the level gate affects Day 1 and Day 7 retention.
- **Predictive Modeling**: Use machine learning to forecast short-term and long-term retention.
- **Actionable Insights**: Provide recommendations for game design, onboarding, and player segmentation using model interpretability techniques.

---

## 📂 Dataset Overview

| Column           | Description                                  |
|------------------|----------------------------------------------|
| `userid`         | Unique user ID                               |
| `version`        | Game version: `gate_30` or `gate_40`         |
| `sum_gamerounds` | Total number of game rounds played           |
| `retention_1`    | 1 if the user returned the next day          |
| `retention_7`    | 1 if the user returned 7 days later          |

---

## 📊 Workflow

1. **Data Exploration**  
   - Bar plots of retention rates  
   - Distribution of gameplay activity

2. **A/B Testing**  
   - Chi-squared test for statistical significance  
   - Conclusion: `gate_40` significantly improves retention

3. **Feature Engineering**  
   - Binned users by gameplay into `low`, `mid`, `high` activity groups  
   - One-hot encoding of categorical variables

4. **Modeling (1-day and 7-day retention)**  
   - Compared 4 models:  
     - Logistic Regression  
     - Random Forest  
     - Gradient Boosting  
     - XGBoost
   - **Gradient Boosting** achieved the highest ROC AUC scores

5. **Model Interpretation**  
   - SHAP values used to explain feature importance  
   - Top features: `sum_gamerounds`, `gameround_group_high`, `version_gate_40`

---

## Key Findings

| Model               | 1-Day ROC AUC | 7-Day ROC AUC |
|--------------------|---------------|---------------|
| Gradient Boosting  | **0.89**      | **0.89**      |
| Logistic Regression| 0.88          | 0.88          |
| XGBoost            | 0.88          | 0.88          |
| Random Forest      | 0.88          | 0.88          |

- **Gradient Boosting is the best model** for predicting both 1-day and 7-day retention.
- `gate_40` significantly improves both short and long-term engagement.
- Users with higher game activity (`sum_gamerounds`) are much more likely to return.

---

## Business Recommendations

- **Gate Strategy**: Shift to `gate_40` for improved onboarding retention.
- **Target High-Value Players**: Segment and reward users with >100 game rounds.
- **Optimize Mid-Engagement Players**: Provide tailored tutorials or incentives.
- **Use Model Interpretability**: Leverage SHAP insights for personalized messaging and targeting strategies.

---

## Possible Extensions

- Hyperparameter tuning (e.g. GridSearchCV)
- Cohort analysis by install date or region
- Streamlit or Dash-based model deployment
- Real-time monitoring dashboard with Tableau/Power BI

---
