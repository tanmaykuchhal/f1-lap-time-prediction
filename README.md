# 🏎️ Predicting F1 Fastest Lap Times — R-Based Regression Analysis

A data science project analyzing Formula 1 race data (2022–present) to predict fastest lap times using machine learning models built in R.

---

## The Question

Can we predict a driver's fastest lap time given what we know *before and during* a race — their starting grid position, pit stop strategy, constructor, and engine manufacturer?

F1 teams spend millions answering versions of this question. We wanted to see how far a well-built statistical model could get.

---

## Dataset

Data sourced from [F1DB](https://github.com/f1db) — an open-source Formula 1 database covering race results, lap times, constructors, and more. Filtered to 2022 onwards to reflect the current technical regulations era.

**Key variables used:**

| Variable | Description |
|---|---|
| `timeMillis` | Fastest lap time in milliseconds (response variable) |
| `gridPositionNumber` | Starting grid position |
| `pitStops` | Number of pit stops during the race |
| `constructorId` | Team (e.g., Red Bull, Mercedes, Ferrari) |
| `engineManufacturerId` | Engine supplier |
| `raceId` | Race/circuit (one-hot encoded to capture track effects) |

---

## Approach

- **Log-transformed** `timeMillis` to reduce skewness and stabilize variance
- **50/50 train/test split** with a fixed seed for reproducibility
- Built and compared multiple models:
  - **Linear Regression** — baseline with grid position and constructor
  - **Interaction Effects** — exploring how grid position × constructor jointly affect lap time
  - **Gradient Boosting** — capturing non-linear patterns in the data
- Evaluated models using **Adjusted R²** and **RMSE**
- Visualized results with **ggplot2** — histograms, box plots, scatter plots, and constructor-level breakdowns

---

## Key Findings

- **Pit stops** added approximately **+7.07%** to lap time on average
- **Grid position** had a measurable effect — cars starting further back tend to post slower fastest laps, likely due to traffic and tire strategy differences
- Constructor and engine manufacturer explained significant variance, reflecting the performance gap between top and midfield teams
- Gradient Boosting outperformed linear models on RMSE, capturing nonlinear relationships that a simple regression missed

---

## How to Run

1. Clone this repo
2. Open `f1-testing.Rmd` in RStudio
3. Make sure the following packages are installed:
```r
install.packages(c("tidyverse", "tidymodels"))
```
4. Place `f1db-races-race-results.csv` in the same directory
5. Knit the R Markdown file to generate the full HTML report

---

## Files

```
├── f1-testing.Rmd                     # Main analysis (R Markdown)
├── f1db-races-race-results.csv        # Raw race data from F1DB
└── README.md                          # You're here
```

---

## Authors

Tanmay Kuchhal — University of Washington
