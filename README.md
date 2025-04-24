# UCSD-SPRINGBOARD-Capstone
Repository for the MLE Capstone Project 

# Predicting Parkinson's Disease Progression from Voice Features

This project uses voice measurement data to predict `total_UPDRS`, a clinical metric of Parkinson’s Disease severity. The dataset includes acoustic features such as jitter, shimmer, and nonlinear measures extracted from sustained vowel phonations by patients with Parkinson's.

## Objective

Develop and evaluate machine learning models to predict the `total_UPDRS` score from voice features in the dataset. This supports the goal of non-invasive, voice-based tracking of Parkinson’s progression.

## Dataset

- Source: [UCI Parkinson's Telemonitoring Dataset](https://archive.ics.uci.edu/ml/datasets/Parkinsons+Telemonitoring)
- Target variable: `total_UPDRS`
- Number of features: 21 voice-based features plus demographic data
- Number of samples: 5,875

## Models Tested

| Model                      | R² Score | MAE   | RMSE  |
|----------------------------|----------|-------|--------|
| Linear Regression          | 0.17     | —     | —      |
| Random Forest Regressor    | 0.95     | 0.72  | 1.61   |
| Gradient Boosting Regressor | ~0.94    | —     | —      |

Full hyperparameter tuning was performed using `GridSearchCV` with 5-fold cross-validation. The best-performing model was Random Forest.

## Cross-Validation

- 5-fold cross-validation used on the training data to assess model generalization.
- Final CV R² scores:  
  `[0.9526, 0.9521, 0.9417, 0.9566, 0.9459]`
  Mean CV R²: 0.9498

## Reproducibility

- All code is in `02_Modeling.ipynb`
- `requirements.txt` included for environment setup
- Random seed fixed across models
- Training/testing split, cross-validation, and metrics are fully reproducible

## Key Learnings

- Random Forest significantly outperformed linear models, suggesting strong nonlinear patterns in the data.
- Voice-based features, especially shimmer and jitter metrics, show a strong correlation with disease severity.
- Cross-validation helped avoid overfitting and confirmed that the model generalizes well.
