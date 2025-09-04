Retail Demand Forecasting

An end-to-end **demand forecasting system** built using **PostgreSQL, Python (Prophet), and Streamlit**.  
It covers the full pipeline from **data ingestion → database → forecasting → evaluation → dashboard**.

---

# Features
- ETL Pipeline: Load transactional sales data (CSV) into a Postgres database.  
- Database Schema: Star-schema with product, store dimensions, and sales fact table.  
- Forecasting: Uses Facebook Prophet for daily demand forecasting.  
- Dashboard: Interactive Streamlit app for product/store forecasts.  
- Model Metrics Logging: RMSE & MAPE stored in Postgres after each forecast.  
- Performance Tab: Explore logged forecasts, errors over time, and trends.  

---

# Project Structure

retail-demand-forecasting/
│
├── data/                          # raw or sample data (ignored in git via .gitignore)
│   └── grocery_chain_data.csv
│
├── sql/
│   └── schema.sql                 # database schema
│
├── src/
│   ├── dashboards/
│   │   ├── __init__.py
│   │   └── app.py                 # Streamlit dashboard
│   │
│   ├── etl/
│   │   ├── __init__.py
│   │   └── load_csv_to_postgres.py
│   │
│   ├── modelling/
│   │   ├── __init__.py
│   │   ├── prophet_forecast.py    # forecasting logic
│   │   └── quick_forecast_from_csv.py
│   │
│   └── utils/
│       ├── __init__.py
│       └── db.py                  # db connection + metrics logging
│
├── notebooks/                     # optional Jupyter/EDA
│
├── requirements.txt               # dependencies
├── README.md                      # project description
├── .gitignore                     # ignore venv, data, pycache
└── retail-demand-forecasting.iml  # IntelliJ project file

# architecture overview
CSV Data  ──►  ETL (Python)  ──►  PostgreSQL
                               │
                               ├───►  Prophet Forecast (Python)
                               │
                               └───►  Streamlit Dashboard
                                        ├── Forecast Tab
                                        └── Model Performance Tab

# running the dashboard
streamlit run src/dashboards/app.py

# Example Output

Local Streamlit dashboard will open at: http://localhost:8501

