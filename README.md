# Predicting EV Charging Infrastructure Needs

## Overview

This project predicts optimal locations for new EV charging stations to support infrastructure planning and accelerate EV adoption. Using clustering and machine learning models, we identify underserved regions and prioritize investments to address accessibility gaps, mitigate range anxiety, and optimize resource allocation.

---

## Table of Contents

- [Background](#background)
- [Clustering Analysis](#clustering-analysis)
- [Prediction Models](#prediction-models)
- [Key Results](#key-results)
- [Recommendations](#recommendations)
- [How to Use](#how-to-use)
- [Data Access](#data-access)
- [Contributors](#contributors)

---

## Background

EVs are rapidly gaining significance, with global sales reaching nearly 14 million units in 2023 (18% of all cars sold worldwide, IEA). However, charging infrastructure often lags behind, creating regional disparities and limiting further adoption. This project identifies where new charging stations are most needed using data-driven methods.

---

## Clustering Analysis

We performed K-Means clustering (k=5) to identify geographic regions with varying EV adoption and charging infrastructure at the ZIP code level.

| Cluster | EV_to_Chargers_Ratio | Total_EV | Total_Chargers | Count_ZIP |
| ------- | -------------------- | -------- | -------------- | --------- |
| 0       | 337.66               | 3859.64  | 18.06          | 47        |
| 1       | 48.25                | 275.39   | 7.08           | 87        |
| 2       | 29.33                | 1735.18  | 65.47          | 17        |
| 3       | 136.28               | 808.29   | 8.06           | 189       |
| 4       | 92.34                | 677.58   | 7.27           | 113       |

**Key Insights:**

- **Cluster 0 (Baltimore-Washington Metro):** Highest EV adoption, but lowest charging infrastructure (EV-to-charger ratio 337.66).
- **Cluster 3 (Central MD/Southern PA):** Moderate EV adoption, sparse infrastructure, largest geographic spread.
- **Cluster 2:** Well-served region with balanced EV adoption and charger deployment.
- **Clusters 1 & 4:** Moderate or low adoption and infrastructure, with potential for future growth.

---

## Prediction Models

We used several machine learning models to classify and prioritize ZIP codes for new charging stations:

### Decision Tree & Random Forest

- **Purpose:** Classify ZIP codes as “Adequately Served” or “Needs New Stations.”
- **Random Forest Accuracy:** 93%
- **Feature Importance:** Total EV registrations and charger count are the strongest predictors.

### Logistic Regression

- **Purpose:** Predicts probability a region is underserved.
- **Accuracy:** 99%, AUC: 1.00
- **Key Coefficients:** More EVs increase need; more chargers decrease need.

### XGBoost

- **Purpose:** High-performance model for prioritizing ZIPs.
- **Accuracy:** 96%, AUC: 1.00
- **Top Features:** Total EVs, charger count, EV growth rate.

#### Sample High-Priority ZIP Codes

| ZIP   | Total_EV | Total EV Chargers | EV_Growth_Rate |
|-------|----------|------------------|----------------|
| 15044 | 2,691    | 8                | 47.21          |
| 19608 | 1,449    | 2                | 1.82           |
| 19606 | 1,437    | 8                | 1.98           |

---

## Key Results

- **Priority Regions:** Cluster 0 and Cluster 3 are most underserved and should be prioritized for infrastructure expansion.
- **High-Priority ZIP Codes:** 161 ZIPs identified by XGBoost for immediate expansion.
- **Feature Importance:** Total EV registrations and charger count are the strongest predictors of infrastructure need.

---

## Recommendations

- **Tier 1 (Immediate Expansion):** Deploy high-capacity charging hubs in high-demand urban ZIPs and expand coverage in suburban/rural areas with critical infrastructure gaps.
- **Tier 2 (Mid-Term Planning):** Systematically expand into additional underserved ZIPs identified by the Random Forest model.
- **Engage Utilities:** Collaborate with utility companies to ensure grid capacity supports planned charging station growth.

---

## How to Use

1. **Data Preparation:** Load the provided dataset (see [Data Access](#data-access)).
2. **Model Training:** Run clustering and predictive models as described above.
3. **Infrastructure Planning:** Use model outputs to prioritize ZIP codes for new charging station deployment.

---

## Data Access

- **Dataset:** [Google Drive Link](https://drive.google.com/drive/folders/1cU3GjIVZwW5VBjZ2XxLVi8irJq4y69iz?usp=sharing)

---

## Contributors

- Vinicius Avelar, Alex Ramos

---

## Acknowledgments

- International Energy Agency (IEA) for EV market data.

---

> For detailed methodology, results, and visualizations, see the full project report.
