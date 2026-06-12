# Swish Analytics Data Modeling Challenge

Predicting the probability that an NFL pass play results in a sack.

## Data Sources
- Play-by-play data
- Rosters
- Depth charts
- Snap counts
- Advanced statistics

## Methods
- Exploratory Data Analysis
- Feature Engineering
- Logistic Regression
- Gradient Boosting

## Author
Ethan Friedman

## Initial Results

A baseline logistic regression model was trained using only game state variables:

- Down
- Yards to go
- Yard line
- Quarter
- Game seconds remaining
- Week
- Expected pass probability (xPass)
- Pass Over Expected (Pass OE)

### Baseline Performance

Model | Features | ROC-AUC

Logistic Regression | Game state features | AUC = 0.574

## ROC Curve

<img src="outputs/figures/baseline_roc_curve.png" width="500">

This serves as the benchmark model for future feature engineering and model improvements.

## Next Steps

- Add offensive and defensive team features
- Incorporate quarterback sack tendencies
- Engineer historical pass-rush metrics
- Train Gradient Boosting models
- Compare feature importance across models

## Improved Performance

Model | Features | ROC-AUC

Logistic Regression | Game state features | AUC = 0.574
Logistic Regression | Game state features + team/QB categorical features | AUC = .603

## Improved ROC Curve

<img src="outputs/figures/improved_roc_curve.png" width="500">

This serves as the new benchmark model for future feature engineering and model improvements.