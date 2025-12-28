# Coffee Shop Sales Data Cleaning & Visualization

This project cleans and explores a **dirty coffee shop sales dataset** (10,000 rows) containing missing values and inconsistent entries such as `ERROR` and `UNKNOWN`.[1]
The notebook demonstrates a complete workflow: load the dataset, assess data quality, clean/impute fields, validate calculations, and create basic summary visualizations.[1]

## Dataset

- Source: Kaggle dataset downloaded inside the notebook using `kagglehub`.[1]
- Example columns used:
  - `Transaction ID`, `Item`, `Quantity`, `Price Per Unit`, `Total Spent`, `Payment Method`, `Location`, `Transaction Date`.[1]
- The notebook calculates data-quality stats across the dataset (nulls + `ERROR` + `UNKNOWN`) and visualizes the distribution.[1]

## Project Files

- `Cleaning-and-visulaizing-Coffee-Shop-Datasets.ipynb` — main notebook (data loading, cleaning, checks, and plots).[1]

## Requirements

Install the typical dependencies used in the notebook (at minimum):[1]

- `pandas`[1]
- `numpy`[1]
- `matplotlib`[1]
- `kagglehub` (to download the dataset programmatically).[1]

Example install:

```bash
pip install pandas numpy matplotlib kagglehub
```

## How to Run

1. Open the notebook:
   - `Cleaning-and-visulaizing-Coffee-Shop-Datasets.ipynb`[1]
2. Run cells in order:
   - The notebook downloads the Kaggle dataset using `kagglehub.dataset_download(...)`.[1]
   - Then it reads `dirty_cafe_sales.csv` into a DataFrame.[1]

## Cleaning Steps (Notebook Logic)

The notebook performs these main cleaning actions:[1]

- **Assess data quality**: counts total cells and computes number of `Null`, `ERROR`, and `UNKNOWN` values across columns, then plots a pie chart.[1]
- **Handle invalid `Item` values**: rows with `Item` in `{error, unknown}` are removed in the notebook.[1]
- **Convert and impute numeric fields**:
  - `Quantity` converted with `pd.to_numeric(..., errors='coerce')`, then missing values filled using item-level median and fallback median.[1]
  - `Price Per Unit` cleaned similarly.[1]
- **Fix `Total Spent`**:
  - Replace `UNKNOWN`/`ERROR` with `NaN`, then fill using `Quantity * Price Per Unit`.[1]
  - Validate inconsistencies by comparing computed vs. recorded totals, then overwrite with the computed total.[1]
- **Standardize categorical columns**:
  - Replace `UNKNOWN`/`ERROR` in `Payment Method` and `Location` with `NaN`.[1]
- **Parse dates**:
  - Convert `Transaction Date` using `pd.to_datetime(..., errors='coerce')`.[1]

## Outputs / Quick Insights

The notebook includes frequency summaries such as value counts for:[1]

- `Location` (e.g., Takeaway vs In-store)[1]
- `Payment Method` (e.g., Digital Wallet, Cash, Credit Card)[1]
- `Item` distribution (e.g., Salad, Juice, Cookie, etc.)[1]

## Notes

- The notebook explicitly avoids dropping all nulls early because the missingness is high.[1]


