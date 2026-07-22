# Data Cleaning with Pandas — NYC Airbnb Open Data

A step-by-step, real-world data cleaning workflow built with Pandas, using the [New York City Airbnb Open Data](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data) dataset from Kaggle (~49,000 listings).

This project walks through identifying and fixing the kinds of problems that show up in almost every real dataset: missing values, duplicate rows, incorrect data types, inconsistent text formatting, and outliers — using Pandas rather than a black-box cleaning library, so every step is transparent and explainable.

📖 Full blog post: [Data Cleaning Made Easy: Best Practices with Pandas (With Real-World Examples)](https://datatodeploy.com/pandas-data-cleaning-guide/)

## Dataset

- **Source:** [Kaggle — New York City Airbnb Open Data](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)
- **File:** `AB_NYC_2019.csv`
- **Size:** ~49,000 rows, 16 columns
- **Contents:** Airbnb listing data across NYC's five boroughs — host info, location, room type, price, minimum nights, review activity, and availability

The dataset isn't included in this repository. Download it within data-cleaning.ipynb file or from Kaggle and place `AB_NYC_2019.csv` in the project root before running the notebook.

## What This Project Covers

- Initial data inspection (`.info()`, `.describe()`, `.describe().T`)
- Identifying and handling missing values (`fillna`, `dropna`, and choosing between them based on what the missingness means)
- Detecting and removing duplicate rows, including full-row and column-subset duplicate checks
- Fixing incorrect data types, including converting `last_review` to a proper datetime with `pd.to_datetime(..., errors='coerce')`
- Standardizing inconsistent text formatting (`.str.strip()`, `.str.title()`, `.replace()`)
- Detecting and visualizing outliers in `price` and `minimum_nights` using the IQR method, with boxplots and histograms
- Cleaning free-text fields with regex (`.str.replace()`)
- Validating the cleaned dataset before saving it

## Getting Started

### Prerequisites

- Python 3.9+
- pandas
- matplotlib

### Installation

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
pip install -r requirements.txt
```

### Usage

1. Download `AB_NYC_2019.csv` from [Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data) and place it in the project root.
2. Open the notebook:

```bash
jupyter notebook data_cleaning.ipynb
```

Or, if you're running it in Google Colab, upload `AB_NYC_2019.csv` to your Colab session or mount it from Google Drive before running the cells.

3. Run all cells in order. The notebook produces a cleaned file, `AB_NYC_2019_cleaned.csv`, at the end.

## Project Structure

```
.
├── data_cleaning.ipynb        # Main notebook — full cleaning workflow
├── AB_NYC_2019.csv            # Raw dataset (not included — download from Kaggle)
├── AB_NYC_2019_cleaned.csv    # Output — generated after running the notebook
└── README.md
```

## Notes

- Some cleaning steps intentionally inject synthetic duplicate rows (matching `host_id`, and separately matching `host_id` + `latitude` + `longitude`) purely to demonstrate how full-row vs. column-subset duplicate detection behaves differently. These are clearly marked in the notebook and are not part of the "real" cleaning pipeline.
- `last_review` is deliberately left as `NaT` for listings with no reviews rather than filled with a placeholder, since there's no meaningful default date for a listing that has never been reviewed.

## License

This project is for educational purposes. The dataset is provided by [Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data) under its associated license — refer to the Kaggle page for usage terms.

## Author

Built by Arash — part of the [datatodeploy.com](https://datatodeploy.com) technical blog covering Python, data science, and deployment.
