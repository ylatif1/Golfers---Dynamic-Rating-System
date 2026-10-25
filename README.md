# Dynamic Rating System for Professional Golfers

In my undergraduate dissertation project, I created a rating system that ranks professional golfers and predicts competition outcomes, with ratings that update dynamically as new results come in.

## The problem
Golf rankings are usually based on points tables that don't display the skill difference between each player or the probability that they win their next competition. I wanted a model that:
- produces an **individual rating for each competitor**, which represents that competitors skill,
- **updates over time** as players compete,
- produces **probabilities** for future outcomes.

## Approach
1. **Data:** Using results from all male **professional tournaments, from 2018 - 2022**, provided by Smartodds (https://www.smartodds.co.uk/)
2. **Model:** Derived a **Generalised Plackett-Luce (GPL)** model from first principles, which uses each **competitors rating, β**, to produce a probability for each tournament outcome.
3. **Dynamic ratings:** Updates each **competitors rating, β**, after each round in a competition. Each competitor also has their own **learning rate, γ**, which helps them reach a realistic rating quickly instead of lagging behind. 
4. **Fitting & validation:** Used R to clean and format the Smartodds data and run the rating algorithm on it.

The code used is shown below, but unfortunately I cannot share the data used, as it is Smartodds confidential data. 

## Results

For the full methodology, maths, alternate models and results, [read the full dissertation](Dissertation.pdf)
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
