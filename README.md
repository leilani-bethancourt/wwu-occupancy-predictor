# WWU Freshman Housing Occupancy Predictor

> A machine learning model to predict on-campus housing occupancy for incoming freshmen at Western Washington University based on enrollment trends and historical patterns.

---

## Overview

Western Washington University's Housing office allocates beds, staffing, and resources based on how many freshmen will live on campus each fall. This project builds a regression model that predicts freshman occupancy counts using enrollment data, yield rates, and historical occupancy trends — giving planners a data-driven forecast before the academic year begins.

**Status:** In progress — data collection phase  
**Target completion:** July 30, 2026

---

## Problem Statement

Each year, WWU must plan housing capacity before final enrollment numbers are confirmed. Over- or under-estimating freshman occupancy leads to either wasted resources or housing shortages. This model aims to provide an early, reliable occupancy forecast using data that is available months before move-in day.

---

## Project Structure

```
wwu-occupancy-predictor/
├── data/
│   ├── raw/               # Original source files (never modified)
│   └── processed/         # Cleaned, feature-engineered data
├── notebooks/
│   ├── 01_eda.ipynb               # Exploratory data analysis
│   ├── 02_feature_engineering.ipynb
│   ├── 03_modeling.ipynb
│   └── 04_evaluation.ipynb
├── src/
│   ├── data_prep.py       # Data loading and cleaning functions
│   ├── features.py        # Feature engineering pipeline
│   └── models.py          # Model training and evaluation
├── outputs/
│   └── figures/           # Generated plots and charts
├── requirements.txt
└── README.md
```

---

## Data Sources

| Source | Description | Access |
|--------|-------------|--------|
| WWU Common Data Set | Annual freshman enrollment, yield rate, housing capacity | Public — `oie.wwu.edu/common-data-set/` |
| WWU Fact Book | Enrollment trends, student profiles | Public — `oie.wwu.edu/factbook/` |
| WWU Housing Office | Historical occupancy records | Internal — provided by department |
| IPEDS | Federally reported enrollment and housing data | Public — `nces.ed.gov/ipeds/` |

---

## Features

| Feature | Description | Type |
|---------|-------------|------|
| `freshman_enrollment` | Total incoming freshman headcount | Numeric |
| `yield_rate` | % of admitted students who enroll | Numeric |
| `housing_capacity` | Total on-campus beds available | Numeric |
| `out_of_state_pct` | % of freshmen from out of state | Numeric |
| `year` | Academic year (temporal index) | Numeric |
| `live_on_required` | Whether first-year live-on policy was in effect | Binary |
| `covid_year` | Indicator for 2020–2021 disruption | Binary |

---

## Models

Models evaluated (planned):

- **Linear Regression** — baseline
- **Random Forest Regressor** — handles nonlinearity, robust to small datasets
- **XGBoost** — gradient boosting; included for comparison
- **Ridge/Lasso Regression** — regularized linear models for small-n settings

Model selection will prioritize interpretability alongside accuracy, since results need to be explainable to a non-technical housing staff audience.

---

## Evaluation Metrics

| Metric | Why |
|--------|-----|
| MAE (Mean Absolute Error) | Interpretable — "off by X beds on average" |
| RMSE | Penalizes large errors more heavily |
| R² | Overall explanatory power |
| Cross-validation (Leave-One-Out) | Appropriate for small datasets |

---

## Setup

```bash
git clone https://github.com/yourusername/wwu-occupancy-predictor
cd wwu-occupancy-predictor

python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

pip install -r requirements.txt
```

Then open `notebooks/01_eda.ipynb` to start.

**Requirements:** Python 3.10+

---

## Key Findings

*To be updated as analysis progresses.*

---

## Limitations

- Dataset is small (~10–20 annual observations), which constrains model complexity
- WWU's first-year live-on requirement, if changed, significantly impacts occupancy independent of enrollment
- COVID years (2020–2021) are treated as outliers and flagged separately
- Model predicts occupancy, not demand — waitlists and housing lottery outcomes are not captured

---

## Author

**[Your Name]**  
B.S. Computer Science / Mathematics — Western Washington University  
[LinkedIn] · [GitHub] · [Email]

---

## Acknowledgments

Data provided in part by the WWU Office of Institutional Effectiveness and WWU University Residences.