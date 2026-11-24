# Can a Model Beat the IMF?

This project predicts next-year real GDP growth for 217 economies from this year's public indicators, and compares machine learning models with simple benchmarks and the IMF's forecasts.

It is a group project for CSC1181 / CSC1203 Machine Learning, Dublin City University, 2026.

## Repository

```
merged_data/
  1181_project_data_merging.ipynb   merges World Bank WDI + IMF WEO, builds the target, makes the time splits
  original_data/                    IMF WEO download (October 2026) and a link to the WDI Excel file
  merged_data/                      the four split CSVs that every other notebook reads
EDA and Statistics/
  EDA_Statistics.ipynb              missing values, distributions, outliers, correlations, hypothesis tests
models/
  GDP_Models_Sami.ipynb             baselines, 4 models, validation, robustness checks, 2026-27 forecasts
  outputs/                          predictions, metrics, forecasts and figures written by the notebook
report/                             report draft (HTML source and PDF)
```

## Setup

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

It was tested with Python 3.14, pandas 3.0, scikit-learn 1.9 and matplotlib 3.11 (Anaconda).

## Run order

1. **Data** (optional; the split CSVs are already in `merged_data/merged_data/`).
   - `merged_data/1181_project_data_merging.ipynb` was written for Google Colab.
   - It needs `WDIEXCEL.xlsx` from the [World Bank WDI download](https://datacatalog.worldbank.org/search/dataset/0037712), placed next to the notebook.
2. **EDA.** `EDA and Statistics/EDA_Statistics.ipynb` runs in Colab. Its first cell asks for a ZIP of the four split CSVs.
3. **Models.** Run `models/GDP_Models_Sami.ipynb` top to bottom (about a minute).
   - It reads the split CSVs and the IMF file through relative paths, and writes everything to `models/outputs/`.
   - No internet is needed: the World Bank country groups are cached in `models/outputs/country_groups.csv`.
   - The forecast settings are at the start of Section 7: `COUNTRIES`, `BASE_2026`, `GROWTH_2026`, `CHANGES` and `ONLY`.

## Method in brief

- **Target and features.** The target is next year's real GDP growth. There are 10 features: 8 indicators plus last year's growth and a 3-year average.
- **Splits by target year.** Train 2001-2017, validation 2018-2019, COVID 2020 kept separate, test 2021-2024. Gaps and scaling are fitted on training rows only.
- **Methods compared.**
  - Baselines: naive (next year = this year), the global mean and the country mean.
  - Models: Ridge, Lasso, Random Forest and Gradient Boosting.
- **Robustness checks.** An expanding-window backtest (2008-2024), a bootstrap over countries, random seeds and ablations.

## Key results

- **Normal years (2008-2019):** the models are about 10% more accurate than the best simple baseline (MAE 2.80 vs 3.11 percentage points).
- **Turning points (2009, 2020, 2021):** no method predicts them. On 2021-2024 the models tie with a plain average.
- **Forecasts:** for 2026, our median country forecast is 3.2% and the IMF's is 3.0%.

## Data

- [World Bank World Development Indicators](https://datacatalog.worldbank.org/search/dataset/0037712) (CC BY 4.0).
- [IMF World Economic Outlook](https://data.imf.org/Datasets/WEO), October 2026 (IMF terms of use).

Both are public, aggregate data with no personal information.

## Team

| Member | Work | Presents |
|---|---|---|
| Farhana Ahmed | Data integration, target and splits, IMF benchmark | Question, data, IMF comparison |
| Sami Haroon Khan | Preprocessing, models, validation, robustness checks, forecasts | Models, validation, forecasts |
| Sukesh Babu Ramesh Babu | Exploratory data analysis and statistics | EDA findings |
| Parthiban Sathappan Tamilselvi | Literature review, error analysis, discussion | Related work, error analysis, limitations |

All four members wrote, edited and reviewed the report together.
