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

- Logistic Regression | Game state features | AUC = 0.584

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

- Logistic Regression | Game state features | AUC = 0.584
- Logistic Regression | Game state features + team/QB categorical features | AUC = .597

## Improved ROC Curve

<img src="outputs/figures/improved_roc_curve.png" width="500">

The addition of team and quarterback context improved predictive performance, suggesting that player and team identity contribute meaningful information beyond game state variables alone

## Historical Sack Tendency Features

To better capture perisistent football tendencies, historical sack rate features were engineered using only training-season data (2021-2022):

- Quarterback Sack Rate
- Offensive Team Sack Rate Allowed
- Defensive Team Sack Rate ALlowed

These features were designed to represent long-term tendencies while avoiding information leakage from the evaluation season.

## Historical Sack Rate Model

Model | Features | ROC-AUC

- Logistic Regression | Game state features | AUC = 0.584
- Logistic Regression | Game state features + team/QB categorical features | AUC = .597
- Logistic Regression | Historical Sack Rate Features | AUC = .605

## Historical Feature ROC Curve

<img src="outputs/figures/improved_roc_curve.png" width="500">

This model directly incorporates football specific tendencies and provides insight into which quarterbacks, offenses, and defenses are most associated with sack outcomes.

## Key Findings

Current results indicate that:

Game-state variables alone provide modest predictive power.
Team and quarterback identity improve model performance.
Historical sack tendencies contain additional predictive signal.
Sack probability appears to be influenced by both situational factors and persistent player/team characteristics.

## Future Work

Planned improvements include:

Gradient Boosting Models
Historical rolling sack-rate features
Offensive line performance metrics
Defensive pass-rush metrics
Feature importance analysis
Model calibration and probability evaluation
Comparison of linear and tree-based models

Current results suggest that sack probability is influenced by both situational factors and persistent team/quarterback tendencies. While historical sack rates improve predictive performance, much of the predictive signal appears to come from game-state variables and quarterback/team context.