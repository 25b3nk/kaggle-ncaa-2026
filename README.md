# March Machine Learning Mania 2026

Kaggle competition entry predicting win probabilities for every possible NCAA basketball tournament matchup (men's and women's), evaluated on log loss.

## Approach

1. **Elo ratings** — updated game-by-game through each regular season (K=20, home advantage adjustment, 75% inter-season reversion toward mean)
2. **Efficiency metrics** — per-team per-season: win%, avg points scored/allowed, point differential
3. **Tournament seed** — numeric 1–16, strongest single predictor
4. **XGBoost classifier** trained on historical tournament games (1985–2025), features as team1–team2 stat differences
5. **Platt scaling** calibration for well-calibrated probabilities
6. Vectorized prediction over all 132K matchups in the submission

CV log loss: **~0.525**

## Structure

```
ncaa_2026.ipynb   # Main notebook (runs end-to-end on Kaggle)
prompt.md         # Competition brief
data/             # Extracted CSV files (not tracked)
venv/             # Python virtual environment (not tracked)
```

## Setup (local)

```bash
python3 -m venv venv
source venv/bin/activate
pip install pandas numpy xgboost scikit-learn jupyter

# Extract competition data to data/
unzip march-machine-learning-mania-2026.zip -d data/

jupyter notebook ncaa_2026.ipynb
```

On Kaggle, the notebook reads from `/kaggle/input/march-machine-learning-mania-2026/` automatically.

## Competition

[March Machine Learning Mania 2026](https://www.kaggle.com/competitions/march-machine-learning-mania-2026)
