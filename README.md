## Malicious-Network-Classification
This notebook builds an optimal Intrusion Detection System (IDS) using the CICIDS 2017 dataset. It uses cost-sensitive learning and feature selection (25 features) to train models. XGBoost emerged as the winner with a 0.9980 F1-score.

link to dataset- https://www.unb.ca/cic/datasets/ids-2017.html

This project implements an optimized Intrusion Detection System (IDS) using the CICIDS 2017 dataset. It focuses on high-performance classification using cost-sensitive learning and efficient feature engineering.

# Key Features
1. Cost-Sensitive Learning: Replaces traditional SMOTE to handle class imbalance more efficiently.
2. Memory Optimization: Downcasts numeric columns and uses stratified sampling to manage the 2.8M+ row dataset within RAM limits.
3. Feature Selection: Reduced the feature set from 78 raw features down to the 25 most impactful variables.
4. Automated Tuning: Utilized Optuna for hyperparameter optimization of the LightGBM mode.

## Model Performance

Evaluated using 5-fold Stratified Cross-Validation:
| Model              | Tuned F1-Score | Recall | AUC    |
|-------------------|----------------|--------|--------|
| XGBoost (Best)    | 0.9980         | 0.9986 | 1.0000 |
| LightGBM          | 0.9973         | 0.9983 | 0.9999 |
| Random Forest     | 0.9969         | 0.9994 | 1.0000 |
| Naive Bayes       | 0.4028         | 0.9848 | 0.8768 |

## Project Artifacts
The pipeline exports the following for deployment (e.g., via Streamlit):

1. best_ids_model.pkl: The trained XGBoost model and optimal decision threshold (0.54).
2. scaler.pkl: StandardScaler fit on the training data.
3. label_info.pkl: Metadata regarding attack types and dataset statistics.
