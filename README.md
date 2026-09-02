# NYC Airbnb Data Cleaning & Preprocessing

Week 1 Task — Virtual Data Science with Python Trainee

## Overview

This project demonstrates data acquisition, cleaning, and preprocessing on a real-world dataset using Python. The dataset is the **New York City Airbnb Open Data (2019)**, originally sourced from Kaggle, containing 48,895 listings across 16 attributes (price, location, room type, host details, review activity, and availability).

## Files

- `clean_data.py` — full cleaning and EDA script (pandas, numpy, matplotlib, seaborn)
- `AB_NYC_2019.csv` — raw input dataset
- `AB_NYC_2019_cleaned.csv` — cleaned output dataset (48,870 rows)
- `Week1_Data_Cleaning_Report.docx` — full written report with methodology, code, and visualizations

## What the script does

1. **Initial exploration** — checks shape, dtypes, missing values, and summary statistics
2. **Missing value handling**
   - `name` / `host_name`: filled with `"Unknown"`
   - `reviews_per_month`: filled with `0` (missing = no reviews, not random)
   - `last_review`: converted to datetime; added a `has_reviews` flag instead of imputing a fake date
3. **Duplicate check** — confirmed no exact duplicate rows
4. **Outlier / erroneous entry handling**
   - Removed 11 listings with `price == 0`
   - Removed 14 listings with `minimum_nights > 365`
   - Capped extreme prices using the IQR method (`price_capped` column) instead of deleting them, to preserve sample size
5. **Feature prep** — converted `neighbourhood_group` and `room_type` to categorical dtype
6. **Visualizations** — missing values chart, price distribution, listings by borough, average price by borough

## How to run

```bash
pip install pandas numpy matplotlib seaborn
python clean_data.ipynb
```

Outputs: `AB_NYC_2019_cleaned.csv` plus four PNG chart files.

## Key results

| Metric | Value |
|---|---|
| Original rows | 48,895 |
| Rows removed (invalid price / minimum_nights) | 25 |
| Final cleaned rows | 48,870 |
| Price outliers capped (IQR method) | 1,328 |

See `Week1_Data_Cleaning_Report.docx` for the full write-up, including rationale for each cleaning decision and its impact on downstream analysis.
