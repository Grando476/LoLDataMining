# League of Legends Games Analysis - Win Prediction

A Data Mining project aimed at predicting the outcome of a League of Legends match (Blue vs. Red team victory) based on statistics from the first 10 minutes of gameplay.

## ⚠️ Important Notice

* **Project Type:** Data taken from Keggle project: https://www.kaggle.com/code/servietsky/league-of-legends-what-to-do-in-first-10-min.
* **Source File:** `ReportDataMining2FinalTB.ipynb`

## 📖 Project Description

League of Legends is a MOBA game where two teams fight to destroy the opposing Nexus. The goal of this project is to investigate which statistics from the early game phase (the first 10 minutes) have the most significant impact on the final victory.

The model attempts to answer the following questions:
* Which early-game actions increase the probability of winning?
* Is it possible to effectively predict the result of a match (usually lasting 30-40 minutes) based on just 10 minutes of data?

## 📊 Dataset

The analysis is based on a dataset containing nearly **10,000 ranked games** from High Elo (Diamond I - Master).
* **Sample size:** ~10k
* **Feature count:** 38 (19 per team)
* **Key features:**
    * `GoldDiff` / `ExperienceDiff`: Difference in gold and experience between teams.
    * `Kills` / `Deaths` / `Assists`: KDA statistics.
    * `Dragons` / `Heralds`: Map objective control (Elite Monsters).
    * `WardsPlaced` / `WardsDestroyed`: Vision control.

## 🛠️ Methodology & Technologies

The project was implemented in **Python** using the following libraries and techniques:

### Technologies
* **Pandas / NumPy:** Data manipulation and cleaning.
* **Seaborn / Matplotlib:** Data visualization (distributions, correlations).
* **Scikit-Learn:** Machine Learning model construction and evaluation.

### Analysis Process
1.  **EDA (Exploratory Data Analysis):**
    * Analysis of variable distributions.
    * Correlation study (e.g., strong correlation between `GoldDiff` and `Winning`).
    * Identification and removal of outliers.
2.  **Feature Engineering:**
    * Creation of new variables, e.g., `DragonControl` (who controlled the dragon), `HeraldControl`.
    * Removal of redundant variables (e.g., removing 'red' stats in favor of 'diff' variables).
3.  **Modeling:**
    * **Decision Trees:** Interpretable baseline model.
    * **Random Forest:** Complex ensemble model for better prediction.
    * **Hyperparameter Tuning:** Using `RandomizedSearchCV` to optimize parameters (e.g., `max_depth`, `n_estimators`).

## 📈 Results & Findings

* **Best Model:** Random Forest / Optimized Decision Tree.
* **Achieved Accuracy:** ~72.27%.
* **Key Findings:**
    * The most important factors influencing victory are **Gold Difference (GoldDiff)** and **Experience Difference (ExperienceDiff)**.
    * A model using only 4 key features (`blueGoldDiff`, `blueExperienceDiff`, `DragonControl`, `redTotalMinionsKilled`) achieved better results than a model using all data, suggesting that many statistics (e.g., ward counts) at the 10-minute mark act as noise.
