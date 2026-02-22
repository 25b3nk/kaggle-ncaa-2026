I'm entering the Kaggle "March Machine Learning Mania 2026" competition.
The goal is to predict win probabilities for every possible NCAA basketball 
tournament matchup (both men's and women's tournaments), evaluated on log loss.

Help me build a complete solution in a Kaggle notebook. Here's what I need:

## Competition context
- Submission format: CSV with columns ID (e.g. "2026_1234_5678") and Pred (probability 0-1)
- Evaluation metric: Log Loss — calibration is critical
- Data: Kaggle provides historical NCAA game results, seeds, team info going back decades
- Both men's (M prefix) and women's (W prefix) tournaments

## What to build
1. **Data exploration** — load and understand all provided CSV files, identify key tables 
   (regular season results, tournament results, teams, seeds)

2. **Feature engineering** — for each team per season, compute:
   - Elo rating (updated game-by-game through regular season)
   - Simple efficiency metrics: points scored/allowed per game, win%, point differential
   - Tournament seed (strong signal)
   - Derived matchup features: Elo difference, seed difference, efficiency deltas

3. **Training dataset** — build a row for every historical tournament game with 
   features for both teams and a binary outcome (1 = lower TeamID won)

4. **Model** — XGBoost classifier trained on historical tournament games, 
   optimized for log loss

5. **Calibration** — apply Platt scaling or isotonic regression to ensure 
   well-calibrated probabilities

6. **Prediction** — generate predictions for all possible 2026 matchups 
   (every team vs every team in the same gender tournament)

7. **Submission file** — output a properly formatted submission.csv

## Constraints
- Everything must run in a single Kaggle notebook session
- Use Python throughout
- Keep it modular so I can swap in better features or models later
- Add markdown cells explaining each section (this needs to be a public notebook)

Start by listing the data files you'd expect to find in /kaggle/input/ and 
ask me to confirm before writing any code.