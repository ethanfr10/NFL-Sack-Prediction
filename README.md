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

<img src="outputs/figures/historical_features_roc_curve.png" width="500">

This model directly incorporates football specific tendencies and provides insight into which quarterbacks, offenses, and defenses are most associated with sack outcomes.

## Key Findings

Current results indicate that:

- Game state variables alone provide modest predictive power.
- Team and quarterback identity improve model performance.
- Historical sack tendencies contain additional predictive signal.
- Sack probability appears to be influenced by both situational factors and persistent player/team characteristics.

## Pre-Snap and Rolling Sack Features

Additional features were engineered to better simulate real pre-snap prediction:

- Season to date quarterback sack rate
- Season to date offensive sack rate
- Season to date defensive sack rate
- Quarterback vs Defense sack risk interaction
- Offense vs Defense sack risk interaction
- Shotgun indicator

These features increased predictive performance by incorporating recent team and quarterback tendencies.

ROC-AUC: 0.611

## Advanced Pressure Statistics

Weekly advanced statistics were integrated into the modeling dataset:

- Quarterback / Offensive Pressure Metrics
- Times Sacked
- Times Pressured
- Times Hurried
- Times Hit
- Times Blitzed
- Pressure Percentage
- Defensive Pressure Metrics
- Defensive Sacks
- Defensive Pressures
- Defensive QB Hits
- Defensive Hurries
- Defensive Blitzes

To avoid information leakage, all advanced statistics are shifted one week so that only information available prior to each game is used.

This feature set is currently being evaluated.

## Rolling Feature ROC Curve

<img src="outputs/figures/rolling_features_roc_curve.png" width="500">

## Current Model Progression
Model | Features | ROC-AUC

- Logistic Regression | Game state features | AUC = 0.584
- Logistic Regression | Game state features + team/QB categorical features | AUC = .597
- Logistic Regression | Historical Sack Rate Features | AUC = .605
- Logistic Regression | Pre-Snap + Rolling Features | AUC =	0.611

Current best model: 0.611 ROC-AUC

## Key Findings

Current results suggest:

- Quarterback sack tendency is one of the strongest predictors of sacks.
- Defensive pass rush tendency provides additional predictive signal.
- Situational football context remains important.
- Recent performance and rolling season tendencies improve prediction beyond long term averages.
- Matchup specific features appear more informative than team identity alone.

## Current Focus

The project is currently focused on integrating advanced pressure metrics, offensive line information, depth chart data, and snap count information to improve predictive performance.

Future iterations will evaluate:

- Advanced pressure features
- Offensive line continuity metrics
- Snap-count based personnel features
- Depth-chart features
- Model calibration
- Feature importance analysis
- Alternative machine learning models


## Author

Ethan Friedman