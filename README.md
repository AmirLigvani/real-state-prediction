# Real Estate Price Prediction

Predicting housing prices with multiple linear regression, using a complete
statistical pipeline: preprocessing, correlation analysis, PCA, and model
evaluation. Developed as a project for the Statistics department at the
University of Tabriz.

## Overview
The project builds and evaluates a price-prediction model on 500 property
records with 10 numeric features, and compares two approaches:

1. **Baseline model:** linear regression on the 10 standardized features
2. **PCA model:** linear regression on the principal components of the same features

## Dataset
500 records, 10 input features, and one target (`Price`):

| Feature | Description |
|---|---|
| Square_Feet | Floor area |
| Num_Bedrooms / Num_Bathrooms / Num_Floors | Room and floor counts |
| Year_Built | Year of construction |
| Has_Garden / Has_Pool | Binary indicators |
| Garage_Size | Garage size |
| Location_Score | Location rating (0–10) |
| Distance_to_Center | Distance to city center (km) |
| **Price** | Target: property price |

## Methodology
- Missing-value check (none found)
- Outlier detection with the IQR method
- Skewness check and conditional log transform
- Conditional winsorization
- Min-Max scaling and standardization
- Pearson correlation analysis (heatmap)
- PCA with explained-variance analysis
- 80/20 train-test split (`random_state=42`)

## Results
| Model | R² (train) | R² (test) |
|---|---|---|
| Linear regression (10 standardized features) | 0.9767 | 0.9709 |
| Linear regression (10 principal components) | 0.9767 | 0.9709 |

- **Square footage** and **number of bedrooms** are the strongest predictors, and
  **year built** is third.
- **Distance to center** has the weakest effect, with a small negative coefficient.
- Variance is spread almost evenly across the 10 principal components (7.7–12.7% each),
  so all 10 are needed to cover 95% of the variance. PCA gave no dimensionality
  reduction benefit, and the two models perform identically.

## Limitations
- The dataset appears to be synthetic: some relationships, such as distance to
  center versus price, don't match real housing-market patterns.
- With only 500 records, the results may not generalize to real-world data.

## Repository contents
- `real estate prediction.ipynb`: code and analysis
- `real_estate_dataset_processed.csv`: the processed dataset
- `گزارش_کار_پیشبینی_قیمت_مسکن.pdf`: full project report (in Persian)

## Tech stack
Python · pandas · NumPy · scikit-learn · SciPy · matplotlib · seaborn

## How to run
```bash
pip install pandas numpy scipy scikit-learn matplotlib seaborn jupyter
jupyter notebook "real estate prediction.ipynb"
```
