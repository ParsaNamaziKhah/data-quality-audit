# Data Quality Audit

This project audits a deliberately messy order dataset with pandas. It checks missing values, exact duplicate rows, unparseable dates, and invalid quantities/prices, then exports a cleaned table and audit files.

## Dataset

`data/messy_orders.csv` is synthetic practice data. Missing values are intentionally present. It is not customer or transaction data from a real company.

## Run it

```bash
pip install -r requirements.txt
```

Open `data_quality_audit.ipynb` in Jupyter Notebook or VS Code and run all cells from top to bottom.

## Main outputs

- `outputs/clean_orders.csv` - rows that pass the cleaning rules
- `outputs/invalid_order_dates.csv` - rows with dates that could not be parsed
- `outputs/invalid_order_values.csv` - rows with a non-positive quantity or negative unit price
- `outputs/cleaning_summary.csv` - row counts at each cleaning stage
- `outputs/missing_values_before_cleaning.csv` and `outputs/missing_values_after_cleaning.csv` - missing-value summaries

## Cleaning decisions

The notebook keeps one copy of each exact duplicate row. It excludes rows with invalid dates, quantity less than or equal to zero, or negative unit price. Missing customer or product values are not automatically imputed because the correct replacement cannot be known from the dataset alone.
