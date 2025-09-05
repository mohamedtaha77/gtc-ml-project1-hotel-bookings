# gtc-ml-project1-hotel-bookings

A compact, reproducible data‑cleaning and preprocessing project on the **Hotel Bookings** dataset.

## Repo Contents
- `notebook.ipynb` — Colab-ready notebook (EDA → Cleaning → Features → Split)
- `hotel_bookings.csv` — raw dataset

## Run in Google Colab
1. Open Colab → New Notebook  
2. Upload `hotel_bookings.csv`  
3. Run all cells  
4. Outputs are saved to files (`hotel_bookings_cleaned_full.csv`, `train_cleaned.csv`, `test_cleaned.csv`)

## Workflow (Phases)
- **Phase 1 – EDA:** `.info()`, `.describe()`, missingness matrix, boxplots, IQR outliers  
- **Phase 2 – Cleaning:** imputations (`company=0`, `agent=0`, `country=mode/Unknown`, `children=median`), drop duplicates, cap outliers (`adr`, `lead_time`), fix dtypes  
- **Phase 3 – Features & Prep:** `total_guests`, `total_nights`, `is_family`, one‑hot for low‑card columns, group/frequency encode `country`, **remove leakage** (`reservation_status`, `reservation_status_date`), train/test split (`test_size=0.2`, `random_state=42`)

## Data Quality 
The dataset shows heavy missingness in **company**, some in **agent/country/children**, many duplicates, and outliers in **adr** and **lead_time**. A few rows are inconsistent (e.g., zero guests but positive nights). **country** is high‑cardinality, so rare codes are grouped. To avoid leakage we drop **reservation_status** and **reservation_status_date** and convert dates to proper datetime. The target **is_canceled** is moderately imbalanced and noted for modeling.
