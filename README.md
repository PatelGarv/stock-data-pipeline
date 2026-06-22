# Stock-Data-Pipeline
End-to-end stock market data pipeline using Alpha Vantage, AWS S3, Databricks, Pyspark and SparkSQL


# Stock Market Data Pipeline
An end-to-end automated data pipeline that pulls real-time stock market data, 
processes it using PySpark, stores it in AWS S3, and runs on a daily schedule 
via Databricks Workflows.

## Architecture
Alpha Vantage API → AWS S3 (Bronze) → Databricks PySpark (Silver) → AWS S3 (Silver) → Logging & Monitoring

## Tech Stack
- **Data Source**: Alpha Vantage API (real-time stock market data)
- **Cloud Storage**: AWS S3 (data lake with Bronze/Silver layers)
- **Processing**: Apache PySpark + SparkSQL on Databricks
- **Orchestration**: Databricks Workflows (Jobs & Pipelines)
- **Scheduling**: Automated daily trigger via Databricks
- **Logging**: JSON logs written to S3 after every run
- **Error Handling**: try/except with FAILED status + error message captured

## Pipeline Stages
- **Bronze Layer**: Raw stock data from Alpha Vantage saved as-is to S3
- **Silver Layer**: Cleaned, typed, deduplicated data saved to S3
- **Logging**: Every run writes a JSON log (run_time, rows_processed, status, error_message)

## Project Structure
stock-data-pipeline/

stock-data-pipeline/

├── notebooks/

│   └── stock_pipeline.ipynb    # Main PySpark ETL notebook

├── docs/

│   └── architecture.md         # Pipeline architecture notes

├── images/

│   └── workflow_screenshot.png # Databricks job screenshot

└── README.md

## Pipeline Screenshots 
![Databricks Workflow)(images/Deskboard_Screenshot_2026_06_22.png)
![S3 Bucket reponce page)(images/S3_bucket_savings_Screenshot_2026_06_22.png)

## How to Run
1. Set up AWS S3 bucket and note your access key + secret key
2. Get a free Alpha Vantage API key at alphavantage.co
3. Import the notebook into Databricks workspace
4. Replace credentials placeholders with your actual values
5. Create a Databricks Job pointing to the notebook
6. Set a daily schedule trigger
7. Click Run now to test

## Key Features
- Fully automated — runs daily with no manual intervention
- Error-resilient — captures and logs failures without crashing
- Scalable — built on PySpark for large data volumes
- Auditable — every run produces a timestamped JSON log in S3


## Author
Garv Patel — M.S. Data Science, Analytics and Engineering, Arizona State University  
GitHub: [PatelGarv](https://github.com/PatelGarv)

