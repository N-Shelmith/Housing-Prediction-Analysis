# Decision Tree Regression - Housing Price Prediction 

## Overview
This project explores the use of **Decision Tree Regression** to predict housing prices and more importantly, to understand how decision trees behave under different levels of model complexity.  
Rather than focusing only on predictive performance, the analysis emphasizes **model judgment**, **overfitting vs underfitting**, **feature importance** and **rule-based interpretability**.


## Objective
- Understand how decision trees work in practice
- Identify key drivers of housing prices
- Observe underfitting and overfitting behavior
- Interpret if–then rules and feature interactions
- Apply regularization to improve generalization


## Dataset
**Housing Price Prediction Dataset**
Housing price dataset with property characteristics such as area, bathrooms, amenities and furnishing status.  
Target variable: **Price** (continuous).


## Methodology

### 1. Data Preparation
- Categorical variables encoded using one-hot encoding
- Data split into training and test sets
- No feature scaling required 


### 2. Models Trained

#### a) Shallow Decision Tree
- `max_depth = 3`
- Purpose: demonstrate **underfitting**
- Result: limited ability to capture structure and interactions

#### b) Deep Decision Tree
- No depth or leaf constraints
- Purpose: demonstrate **overfitting**
- Result: near-perfect training performance but poor generalization

#### c) Regularized Decision Tree (Final Model)
- `max_depth = 6`
- `min_samples_leaf = 10`
- Purpose: balance bias and variance
- Result: best generalization performance and interpretable rules


## Model & Results

| Model              | Train R² | Test R² | Train RMSE | Test RMSE |
|-------------------|----------|---------|------------|-----------|
| Shallow Tree      | 0.58     | 0.38    | 1.14M      | 1.78M     |
| Deep Tree         | 1.00     | 0.48    | 0.07M      | 1.63M     |
| Regularized Tree  | 0.69     | 0.51    | 0.98M      | 1.57M     |

**Key takeaway:**  
The regularized tree provides the best trade-off between predictive performance and generalization.


## Feature Importance (Regularized Tree)

- **Area** is the strongest driver of price, acting as the primary market segmenter.
- **Bathrooms** further differentiate prices within size categories.
- Amenities such as **air conditioning, parking, furnishing status, and guest rooms** refine prices within established segments.
- Features with near-zero importance did not meaningfully reduce prediction error under the imposed constraints.

Feature importance reflects **error reduction across splits**, not per-unit effect sizes.


## Rule-Based Interpretation (If–Then Logic)

The regularized tree produces intuitive pricing rules, for example:

- Larger houses are priced in a different range than smaller houses.
- Within large houses, the number of bathrooms and amenities such as air conditioning and parking significantly influence price.
- Amenities matter conditionally, depending on size and layout.

This highlights how decision trees naturally model **feature interactions** and conditional effects.


## Key Learnings

- Decision trees split data using thresholds rather than linear relationships.
- Feature importance measures usefulness for reducing error, not magnitude of effect.
- Shallow trees underfit; deep trees overfit.
- Regularization is essential for generalization.
- Decision trees provide interpretable, rule-based insights aligned with real-world reasoning.


## Conclusion

This analysis demonstrates that while decision trees are powerful and interpretable, they require careful control of complexity to avoid memorization. A regularized decision tree achieves the best balance between accuracy, stability and interpretability, making it suitable for exploratory pricing analysis and decision support.

