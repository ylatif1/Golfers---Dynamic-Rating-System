# Dynamic Rating System for Professional Golfers

My undergraduate dissertation (BSc Mathematics & Statistics, Newcastle University). A rating system that ranks professional golfers and predicts competition outcomes, with ratings that update dynamically as new results come in.

## The problem
Golf rankings are usually based on points tables that don't directly give you a probability of who will win next week. I wanted a model that:
- uses the **full finishing order** of each tournament, not just winners
- **updates over time** as form changes
- produces **probabilities** for future outcomes

## Approach
1. **Model:** Derived a **Generalised Plackett-Luce (GPL)** model from first principles. Plackett-Luce models a ranking as a sequence of choices: the winner is "chosen" from the whole field in proportion to their strength, then second place from those remaining, and so on.
2. **Dynamic ratings:** <!-- Describe how ratings update over time, e.g. time-weighting older results, a state-space / Kalman-style update, or refitting on a rolling window. -->
3. **Data:** Four years of professional competition results. <!-- Source, e.g. which tour(s), number of tournaments and players. -->
4. **Fitting & validation:** Implemented in R. <!-- How you estimated parameters (e.g. maximum likelihood, MM algorithm) and how you validated (e.g. train on years 1–3, test on year 4; log-loss or accuracy vs. official rankings). -->

## Results
<!-- Add 2–4 concrete results. Examples of what to show:
- Out-of-sample log-likelihood / accuracy compared with a baseline (e.g. official world ranking)
- How often the model's top-10 favourites finished top 10
- A chart of one player's rating over time
- Example predicted win probabilities for a real tournament
-->

## Repository structure
```
golf-rating-model/
├── data/            # cleaned results (or a script to download them)
├── R/
│   ├── clean_data.R
│   ├── fit_gpl.R
│   └── predict.R
├── figures/         # rating-over-time plots, calibration charts
├── dissertation.pdf # optional: full write-up
└── README.md
```

## How to run
```r
source("R/clean_data.R")
source("R/fit_gpl.R")
source("R/predict.R")
```

## What I learned
- Deriving a likelihood from first principles and implementing it myself rather than relying on a package
- Handling messy sports data (withdrawals, missed cuts, ties)
- Turning a statistical model into usable predictions
