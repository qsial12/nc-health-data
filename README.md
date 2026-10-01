# NC Health Data Products

Health data products for North Carolina, built in public over 26 weeks while relearning data science for medical analytics.

**Rule:** this repo uses only public and synthetic data. No real patient records, no credentialed research datasets, no data under non-commercial licences in anything intended for sale.

## Data sources

| Source | Release | Downloaded | Licence / terms | Used in |
| --- | --- | --- | --- | --- |
| [CDC PLACES](https://www.cdc.gov/places/tools/data-portal.html), census tract data, NC | 2025 | 2026-09-30 | Public domain (federal) | Week 1 |
| [CDC PLACES](https://www.cdc.gov/places/tools/data-portal.html), county data, NC | 2025 | 2026-09-30 | Public domain (federal) | Week 1 |

Survey year(s) in the PLACES files: [fill in from `raw["Year"].value_counts()`]

Raw files live in `data/raw/` and are not committed to Git (see `.gitignore`). To reproduce, download them as described below.

## Limits of the data

- **PLACES values are modeled estimates**, built from the BRFSS survey plus census demographics. They are not counts of diagnosed patients, and extremes are smoothed toward the average.
- **Findings describe census tracts, not individuals.** A correlation between tracts says nothing directly about any one person (the ecological fallacy).
- **Tract values are crude prevalence.** County files also offer age-adjusted prevalence; comparisons state which one is used.
- Tracts with fewer than 500 people or very wide confidence intervals are flagged as `unstable` and excluded from top/bottom rankings.

## Setup

**Windows (Command Prompt)**

```bat
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
mkdir data\raw data\processed notebooks figures
```

**Mac / Linux**

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdir -p data/raw data/processed notebooks figures
```

**Get the data:** on the CDC PLACES data portal, open the latest Census Tract Data release, filter `StateAbbr` to `NC`, export as CSV and save as `data/raw/places_tract_nc.csv`. Repeat for County Data as `data/raw/places_county_nc.csv`.

## Repo structure

```
data/raw/          downloaded source files (not committed)
data/processed/    cleaned outputs from notebooks
notebooks/         one notebook per week
figures/           charts used in posts and reports
```

## Progress

| Week | Topic | Notebook | Status |
| --- | --- | --- | --- |
| 1 | pandas, distributions: NC tract profile of diabetes, obesity, high blood pressure | `notebooks/01_places_nc_profile.ipynb` | In progress |
