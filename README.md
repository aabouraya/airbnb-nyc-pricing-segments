# Airbnb NYC 2019 — Track 1 (Classical ML: Regression & Clustering)

Group A team project. Business question (draft):

> What types of hosts do we have in NYC, and what drives the price of their listings,
> so Airbnb can give each type of host better pricing advice?

## Project structure

```
airbnb-nyc-pricing-segments/
├── data/
│   ├── raw/AB_NYC_2019.csv      # original Kaggle file — never edit
│   └── processed/               # cleaned data written by notebooks
├── notebooks/                   # Jupyter / Colab notebooks (empty for now)
├── reports/figures/             # charts used in the report
├── decisions.md                 # every cleaning/modelling decision and why
├── requirements.txt
└── README.md
```

## Getting started

### Option A: local
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook notebooks/
```

### Option B: Google Colab
1. Open the notebook in Colab (File → Open notebook → GitHub, once the repo is on GitHub).
2. Run the first cells. If the dataset is not found, the notebook asks you to upload `AB_NYC_2019.csv`.

## Reproducibility
- Random seed: `42` everywhere.
- All numbers in the report must come from these notebooks.
- Record each decision in `decisions.md`.

## Data
`AB_NYC_2019.csv` — Inside Airbnb / Kaggle: New York City Airbnb Open Data (2019).
48,895 listings × 16 columns.

## Acknowledgments
The initial project structure and boilerplate code for this repository were generated with the assistance of Claude Code (by Anthropic).