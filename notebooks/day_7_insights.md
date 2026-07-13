# Day 7 - Deep Analysis and Insights

Day 7 is about turning charts and cleaned data into decisions for the future model. The goal is not to train yet, but to identify which variables seem useful for predicting semifinal-level performance.

## Insight #1: Deep runs are strongly linked to match volume and wins

**What I found:** The strongest correlations with the temporary `deep_run` target are `matches_played` (0.81), `wins` (0.69), `goals_for` (0.62), and `goal_difference` (0.49).

**What it means for the model:** The model should include variables that measure consistency across a tournament, not only attacking output.

**Derived variable:** `deep_run` and future official `reached_semifinals` target.

## Insight #2: Goal difference is a better success signal than goals alone

**What I found:** `goal_difference` is strongly related to `win_percentage` (0.80) and is also one of the strongest variables related to deep runs.

**What it means for the model:** Teams that score more than they concede should receive stronger semifinal probabilities.

**Derived variable:** `goal_difference`.

## Insight #3: UEFA and CONMEBOL dominate historical performance

**What I found:** UEFA and CONMEBOL have the highest average win percentages, both around 41.8%, and positive average goal differences.

**What it means for the model:** Confederation should be tested as a categorical predictor because historical strength is not evenly distributed.

**Derived variable:** `confederation`.

## Insight #4: Home teams score more than away teams in the match dataset

**What I found:** Home and away average goals can be compared from `clean_partial.csv` to measure role-based scoring differences.

**What it means for the model:** Venue role may affect match-level performance, but it should be used carefully for tournament-level predictions.

**Derived variable:** `venue_role`.

## Insight #5: Brazil and Germany are the strongest historical teams

**What I found:** Brazil has 70 wins and Germany has 66 wins, clearly ahead of the rest of the historical ranking.

**What it means for the model:** Historical success should be included because repeated World Cup performance is a strong signal.

**Derived variable:** `historical_win_percentage`.
