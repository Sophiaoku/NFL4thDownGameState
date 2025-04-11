# Winning Strategies: Analyzing 4th Down Tactics in American Football <br />

## Project Summary <br />

This project applies data mining and statistical learning to analyze fourth-down decision-making in the NFL. Using NFL play-by-play data from 2016–2023, we developed models to evaluate the strategic options teams face on 4th down: **go for it**, **punt**, or **kick a field goal**. <br />

Our hypothesis: **NFL teams are overly conservative on 4th down**, going for it less often than analytics suggest they should.<br />



## Objectives

- Predict the **optimal fourth-down decision** based on game state variables (yard line, time remaining, score differential, etc.).<br />
- Quantify how often NFL teams follow or deviate from the model-recommended decision.<br />
- Simulate the expected win probability impact of each 4th-down play choice.<br />
- Provide data-driven insights into improving in-game decision-making.<br />



## Data & Tools

- **Data Source**: NFL play-by-play data from 2016 to 2023, accessed using [`nfl_data_py`](https://pypi.org/project/nfl-data-py/).<br />
- **Features Used**: After filtering 384 initial variables, 12 key game-state features were selected for modeling.<br />
- **Analysis Tools**:
  - Python (Pandas, Scikit-learn, XGBoost, Logistic Regression, etc.) <br />
  - K-means Clustering <br />
  - Generalized Additive Models (GAM)<br />
  - Inverse Transform Sampling for Simulation<br />


## Methodology<br />

### 1. **Win Probability Model**  <br />
We trained multiple models (Logistic Regression, GAM, Random Forest, XGBoost) to estimate a team’s probability of winning a game based on current in-game conditions. <br />
**Best model**: XGBoost (MAE ≈ 1.27%).<br />

### 2. **Probability Estimations**<br />
- PMFs were built for each 4th-down action (`go for it`, `punt`, `field goal`) using K-means clustering and play outcomes.<br />
- A **logistic regression model** was used to predict field goal success probability.

### 3. **Simulation Model**
A simulation engine compares pre-play win probability with the simulated outcomes of each play type.<br />
**Goal**: Choose the play that maximizes win probability.<br />


## Key Findings <br />

- **NFL teams go for it less frequently** than the model recommends.<br />
- Teams consistently **prefer field goals** even when simulations suggest higher expected win probabilities from going for it.<br />
- **10 teams** were more aggressive than optimal, **21 teams** were more conservative.<br />
- Going for it tends to be optimal **near the opponent's red zone** and in **late-game scenarios**.<br />


## Results

- Evaluated 3,605 filtered 4th-down plays from the 2023 season.<br />
- Simulated expected win probabilities across different game states and compared to actual play calls.<br />
- Created heatmaps and bar charts showing optimal vs. actual decisions by team and play type.<br />


## Future Work

- Incorporate **team-specific tendencies** for more personalized recommendations.<br />
- Expand the interface for real-time querying or **season-wide team comparisons**.<br />
- Improve handling of edge cases and broaden training data to earlier seasons pre-2016.<br />


## Authors

- Patrick McGee<br />
- Victor Ye <br />
- Sophia Oku <br />
- Andrew McAlister<br />
- Pranay Shah <br />


## References

- Yurko, R., Ventura, S., & Horowitz, M. (2018). *nflWAR: a reproducible method for offensive player evaluation in football*. JQAS.  
- Burke, B. (2014). *Win Probability Model*. Advanced Football Analytics.  
- Lock & Nettleton (2014). *Random Forests for NFL Win Probabilities*.  
- [`nfl_data_py`](https://pypi.org/project/nfl-data-py/), [`NFLfastR`](https://nflverse.nflverse.com/)

### Quick Links to Folders

- [Code](./Code/) Model training, evaluation, and utility scripts <br />
- [Reports](./Reports/) Project reports and presentation materials <br />
- [Docs](./Docs/) Supporting literature and PDFs <br />

