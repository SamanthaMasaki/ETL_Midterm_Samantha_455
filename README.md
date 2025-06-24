# ETL_Midterm_Samantha_455
Project that show ETL pipeline
## ETL Pipeline Breakdown

### 1. Extract – `etl_extract.ipynb`  
- Loaded `raw_data.csv` and `incremental_data.csv` using pandas  
- Displayed `.head()` & `.info()` to inspect data quality, types, and row counts  
- Documented observations: missing values, duplicates, data type issues  
- Saved raw files into `data/` for reproducibility  


### 2. Transform – `etl_transform.ipynb`  
Applied at least **four meaningful transformations** to both datasets:

1. Cleaning – Dropped duplicate rows and/or handled missing values  
2. Enrichment – Derived a `total_price` column = `quantity * unit_price` .   tells us how much money was made per transaction.
3. Structural – Converted `order_date` to datetime; cast IDs to integer .  Dates must be in datetime format for filtering, grouping, or time-series analysis.Ensuring columns have the correct data types prevents future errors during loading or querying
4. Categorization – Created loyalty tiers (Bronze/Silver/Gold) based on purchase counts . Reduces noise and file size. Columns that aren’t needed for analysis should be dropped.

Each transformation includes:
- Before/after display via `.head()`
- Clear explanation of why it was necessary
- Outputs saved as:
  - `transformed/transformed_full.csv`
  - `transformed/transformed_incremental.csv`


### 3. Load – `etl_load.ipynb`  
Loaded transformed CSVs into a chosen format:

| Format    | File(s)                                  | Verification                  |
|-----------|-------------------------------------------|-------------------------------|
| **Parquet** | `full_data.parquet`, `incremental_data.parquet` | `pandas.read_parquet().head()`  |

Results verified via SQL queries or `.head()`


## Additional Tools  
- Python 3.10+ 
- Jupyter Notebook 
- pandas library  
- pyarrow for Parquet   


