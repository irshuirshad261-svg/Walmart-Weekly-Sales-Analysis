# Walmart Weekly Sales Analysis and Predictive Modelling

## Project Overview

This project explores historical weekly sales data from 45 Walmart stores to identify sales patterns, examine relationships between sales and external factors, and develop Linear Regression models to estimate weekly sales.

The project demonstrates an end-to-end analytical workflow using Python, including data preparation, exploratory data analysis, statistical testing, regression diagnostics and model evaluation.

## Business Problem

Understanding weekly sales variations across retail stores is important for effective business and operational planning.

Sales can vary due to store-level differences, holiday periods and external economic factors. This project investigates these relationships and evaluates how well selected variables explain variations in weekly sales.

## Project Objectives

- Analyze weekly sales patterns across different stores.
- Investigate the relationship between sales and holidays, temperature, fuel prices, CPI and unemployment.
- Identify patterns and relationships through exploratory data analysis.
- Develop and evaluate Linear Regression models.
- Assess regression assumptions and multicollinearity.
- Compare alternative model specifications and identify a candidate for further validation.

## Dataset Overview

| Attribute | Details |
|---|---|
| Records | 6,435 |
| Stores | 45 |
| Observations per store | 143 |
| Original features | 8 |
| Target variable | Weekly_Sales |

**Features include:**
- Store
- Date
- Weekly_Sales
- Holiday_Flag
- Temperature
- Fuel_Price
- CPI
- Unemployment

*Note: The raw dataset is not included in this repository. Please refer to the original dataset source for access and usage permissions.*

## Tools and Technologies

- **Python** – Analytical programming
- **Pandas & NumPy** – Data manipulation and preparation
- **Matplotlib & Seaborn** – Data visualization
- **Statsmodels** – Statistical analysis and regression diagnostics
- **Scikit-learn** – Model evaluation and data splitting
- **Jupyter Notebook** – Analysis and documentation
- **GitHub** – Project version control and portfolio

## Project Workflow

1. **Data Understanding and Preparation:** Examined dataset structure, data types, missing values and duplicate records. Created additional date-related features for analysis.
2. **Exploratory Data Analysis:** Investigated sales distributions, store-level variations, holiday effects and relationships with external variables.
3. **Feature Preparation:** Prepared categorical store variables using one-hot encoding.
4. **Model Development:** Built two Ordinary Least Squares (OLS) Linear Regression models.
5. **Model Evaluation:** Compared training and test performance using R², MAE and MSE.
6. **Regression Diagnostics:** Examined residual patterns, normality, multicollinearity, heteroscedasticity and residual independence considerations.
7. **Model Comparison:** Evaluated the impact of removing CPI on model performance and multicollinearity.

## Model Comparison

Two models were evaluated using the same random 70:30 train-test split.

| Evaluation Metric | Model 1 (With CPI) | Model 2 (Without CPI) |
|---|---:|---:|
| Train R² | 0.9203 | 0.9201 |
| Test R² | 0.9188 | 0.9189 |
| Train MAE | 91,679 | 91,446 |
| Test MAE | 91,581 | 91,157 |

### Key Findings

- Both models achieved comparable R² values.
- Model 2 showed a marginal improvement in test MAE.
- Removing CPI substantially reduced VIF values for many store indicator variables.
- CPI had an exceptionally high VIF of approximately 414.69 in Model 1.
- After removing CPI, the VIF for Unemployment remained elevated at approximately 13.37.

### Preliminary Model Selection

Model 2, without CPI, was selected as the preferred candidate for further evaluation.

It maintained comparable predictive performance while substantially reducing multicollinearity among several predictors.

## Regression Diagnostics

The baseline regression model was evaluated using:

- Residuals vs Fitted plot
- Residual distribution and Q-Q plot
- Variance Inflation Factor (VIF)
- Breusch-Pagan test for heteroscedasticity
- Durbin-Watson statistic

The diagnostics indicated:

- Evidence of non-normal residuals.
- Evidence of heteroscedasticity based on the Breusch-Pagan test.
- High multicollinearity involving CPI, Unemployment and several store indicators.
- Further investigation required to assess residual independence over time.

HC3 heteroscedasticity-robust standard errors were also examined to obtain more reliable coefficient inference under heteroscedasticity.

## Limitations and Future Improvements

- Perform chronological train-test validation to evaluate performance on future periods.
- Investigate remaining multicollinearity involving Unemployment.
- Explore additional features that may explain sales variations.
- Evaluate alternative regression and machine learning algorithms.
- Investigate time-series modelling approaches where appropriate.

## Repository Contents

- `Walmart_Weekly_Sales_Analysis.ipynb` – Complete analytical workflow, visualizations, statistical tests and modelling.
- `README.md` – Project overview, methodology and findings.

---

**Project Status:** Initial analysis and model comparison completed. Chronological validation remains a planned improvement.
