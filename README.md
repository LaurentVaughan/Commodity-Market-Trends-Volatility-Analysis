# Commodity Futures Analysis – Data Engineering Capstone

This capstone project demonstrates a complete end-to-end data engineering workflow using a real-world dataset of commodity futures prices. The pipeline covers extraction, transformation, loading, and visualization stages using industry-standard tools like Python, Pandas, SQLite/PostgreSQL, and Streamlit.

---

## Project Objective

The objective is to build a robust and scalable data pipeline that ingests a substantial dataset of commodity futures, cleans and transforms it for analysis, stores it efficiently, and surfaces key insights through interactive visualizations.

---

## Dataset

- **Name:** Commodity Futures Prices (Expanded)
- **Size:** ~12,000 records across 24 columns
- **Features:** Daily prices for 23 global commodities including oil, gas, metals, and agricultural products.
- **Source:** (Replace with actual source if applicable)

---

## Key Analytical Questions

1. Which commodities exhibit the highest price volatility over time?
2. How have the prices of major commodities trended in recent years?
3. Are there observable correlations among energy, metals, and agricultural commodities?
4. Can we detect price anomalies or spikes that may correspond with global events?

---

## Tech Stack

- **Python 3.10+**
- **Pandas** – for data transformation
- **SQLite / PostgreSQL** – for data persistence
- **Streamlit** – for building interactive dashboards
- **Pytest / Unittest** – for testing

---

## ETL Workflow

1. **Extract**: Load CSV data from local storage.
2. **Transform**:
   - Handle missing values
   - Normalize and aggregate data
   - Compute daily percent change and volatility metrics
3. **Load**:
   - Store cleaned and enriched data into SQLite (development)
   - Use PostgreSQL/Pagila schema for production simulation

---

## Visualizations (Streamlit Dashboard)

- **Commodity Price Trends**: Line chart with filterable date ranges
- **Volatility Ranking**: Bar chart of standard deviation of returns
- **Correlation Heatmap**: Relationship matrix between selected commodities
- **Anomaly Detection**: Highlight days with price spikes or unusual drops

Access the deployed Streamlit app here: [Your App URL]

---

## Testing

- TDD applied to transformation functions
- Tests written using `pytest`
- Coverage includes data cleaning, aggregation, and anomaly detection

---

## Folder Structure

```
commodity-futures-capstone/
│
├── .commodities_venv/              # Python virtual environment
│
├── data/
│   ├── raw/
│   │   └── commodity_futures_expanded.csv   # Original source CSV file
│   └── processed/
│       └── transformed_commodities.csv      # Output after ETL
│
├── src/
│   ├── extract.py                   # Loads raw data into a DataFrame
│   ├── transform.py                 # Cleans and enriches the data
│   ├── load.py                      # Writes processed data to PostgreSQL
│   ├── db_utils.py                  # Manages DB connection and helper functions
│   └── config.py                    # Constants or configurations (e.g., column names)
│
├── streamlit_app/
│   ├── dashboard.py                 # Entry point of the Streamlit app
│   └── components/
│       ├── price_trends.py         # Line chart for commodity prices
│       ├── volatility_view.py      # Bar chart showing volatility
│       └── correlation_heatmap.py  # Heatmap for correlations
│
├── tests/
│   ├── test_transform.py           # Unit tests for data transformation
│   ├── test_extract.py                 # Tests for src/extract.py
│	├── test_transform.py              # Tests for src/transform.py
│	├── test_load.py                   # Tests for src/load.py
│	├── test_dashboard.py              # Tests logic in streamlit_app/dashboard.py
│	└── components/
│	    ├── test_price_trends.py       # Tests for data logic in price_trends.py
│	    ├── test_volatility_view.py    # Tests for volatility chart logic
│	    └── test_correlation_heatmap.py# Tests for correlation heatmap generation
│
├── notebooks/
│   └── 01_eda.ipynb                # Jupyter notebook for initial exploration
│
├── .env                            # Environment variables (not committed)
├── .gitignore                      # Ignores data files, venv, .env, etc.
├── README.md                       # Project documentation
├── requirements.txt                # Python dependencies
└── run_pipeline.py                 # Script to run the full ETL pipeline

```

---
## Optimization & Performance

If the dataset grows significantly:
- Use chunked reads for large CSVs with `pandas.read_csv(chunksize=...)`
- Index key columns in the database (e.g., date, commodity)
- Use multiprocessing for transformation steps
- Cache transformed data with joblib or feather format

---

## Error Handling & Logging

- Custom logging using Python’s `logging` module
- Errors caught during transformation are logged with context (e.g., row number, column)
- Graceful handling of nulls and type mismatches

---

## Security & Privacy Considerations

- No personal data present
- If deployed to the cloud, environment variables are used for DB credentials
- Use SSL for database and dashboard connections

---

## Cloud Deployment Strategy (Optional)

To deploy this pipeline in the cloud:
- **S3** for raw/processed data storage
- **AWS Lambda** or **Glue** for transformation tasks
- **RDS PostgreSQL** for data persistence
- **CloudWatch** for monitoring logs
- Containerize the Streamlit app with Docker and deploy via **ECS** or **App Runner**

---

## Learner Stories

- As a data engineer, I designed and implemented a complete ETL pipeline.
- I used Pandas for data transformation and Streamlit for interactive insight sharing.
- My project demonstrates readiness for real-world data engineering challenges and is publicly documented on GitHub for portfolio purposes.

---
