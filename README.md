# March Madness Betting Analytics

An end-to-end sports analytics project that predicts NCAA March Madness game outcomes using multivariate statistics and machine learning, then translates predicted win probabilities into risk-adjusted bet sizes using the Kelly Criterion.

## Project Overview

March Madness presents an interesting prediction problem: teams differ across dozens of offensive, defensive, efficiency, shooting, rebounding, and strength-of-schedule metrics, but only a subset meaningfully contributes to tournament outcomes.

This project develops a reproducible modeling pipeline using historical KenPom and BartTorvik statistics to:

- Engineer team-level matchup differences
- Identify predictive variables using LASSO regularization
- Investigate multivariate relationships using MANOVA
- Estimate win probabilities with logistic regression
- Evaluate performance on future tournament seasons
- Convert model probabilities into fractional Kelly bet sizes

## Model Performance

To reduce temporal leakage, the model was trained on tournament seasons through **2022** and evaluated on a chronological holdout consisting of **2023–2025** games.

| Metric | Holdout Performance |
|---|---:|
| Accuracy | **74.05%** |
| Sensitivity | **76.24%** |
| Specificity | **71.43%** |

### Holdout Confusion Matrix

| Actual / Predicted | Loss | Win |
|---|---:|---:|
| Loss | 60 | 24 |
| Win | 24 | 77 |

Unlike a random train/test split, this evaluation asks a more realistic question:

> Can a model trained on past NCAA tournaments generalize to tournaments that occur later?

## Modeling Pipeline

Historical Tournament Data
        ↓
KenPom + BartTorvik Metrics
        ↓
Matchup Feature Engineering
        ↓
Chronological Train/Test Split
        ↓
Correlation Analysis
        ↓
LASSO Feature Selection
        ↓
Multivariate Analysis (MANOVA)
        ↓
Logistic Regression
        ↓
2023–2025 Holdout Evaluation
        ↓
2026 Win Probabilities
        ↓
Fractional Kelly Bet Sizing

## Betting Strategy

The logistic regression model produces estimated win probabilities rather than only binary predictions.

These probabilities can be compared with implied sportsbook probabilities to estimate potential betting edges. The Kelly Criterion provides a framework for translating those edges into bankroll allocations.

A fractional Kelly strategy is included to reduce the volatility associated with full-Kelly betting.

**Important:** The betting component is a modeling and simulation framework. It should not be interpreted as evidence of realized investment returns or guaranteed betting profitability.

## Tools & Methods

**Language:** R

**Statistical & ML Methods:** Logistic Regression, LASSO Regularization, MANOVA, Multivariate Normality Analysis, Correlation Analysis, Kelly Criterion

**Libraries:** `dplyr`, `glmnet`, `corrplot`, `MVN`

**Data:** NCAA tournament matchups with KenPom and BartTorvik team statistics

## Repository Structure

march-madness-betting-analytics/
├── analysis/
│   └── march_madness_analysis.Rmd
├── data/
│   ├── KenPom_Barttorvik.csv
│   ├── Tournament_Matchups.csv
│   └── README.md
├── figures/
├── results/
├── report/
│   └── Optimal_Bet_Sizing_March_Madness_Project_Report.pdf
├── README.md
└── LICENSE

## Key Takeaway

The project demonstrates how statistical modeling can move beyond predicting a binary outcome. By combining feature selection, interpretable probability modeling, out-of-sample validation, and bankroll optimization, the analysis connects predictive analytics with decision-making under uncertainty.

The final logistic regression model achieved **74.1% accuracy on NCAA tournament games from 2023–2025 that were excluded from model training**.

## Disclaimer

This project is intended for educational and analytical purposes only. Betting examples and Kelly Criterion calculations are simulations and do not constitute financial or gambling advice.
