# DataPipeline-AWS-1st-project
Purpose: Showcase an automated ETL pipeline that extracts data from MySQL, transforms it, uploads to S3, and loads into Redshift. Intended for interview/demo use and HR review.

## Client Problem
Client stores sales and customer data across multiple MySQL instances. Reporting is manual and slow; stakeholders need consolidated daily analytics.

## Client Objective
Automate extraction, transformation, and loading of data into a centralized Redshift data warehouse for analytics and dashboards.

## Solution Overview
- Extract from MySQL using Python scripts.
- Transform data with Pandas (cleaning, deduplication, typing).
- Upload processed files to AWS S3 as parquet/csv.
- Use Redshift COPY command to load data from S3.
- Orchestrate and schedule with Apache Airflow DAGs.

## Repo structure
```
DataPipeline-AWS-1st-project/
├── dags/
│   └── etl_mysql_to_s3_redshift_dag.py
├── scripts/
│   ├── extract_mysql.py
│   ├── transform_data.py
│   ├── load_to_s3.py
│   └── load_to_redshift.py
├── config/
│   ├── aws_credentials.yml.example
│   ├── redshift_config.yml.example
│   └── mysql_config.yml.example
├── data/
│   └── sample_orders.csv
├── requirements.txt
├── .gitignore
└── README.md
```

## How to use (short)
1. Fill `config/*.yml` with your credentials (do NOT commit secrets).
2. Create and activate a Python virtualenv, then `pip install -r requirements.txt`.
3. Start Airflow (local) and place `dags/etl_mysql_to_s3_redshift_dag.py` into your DAGs folder.
4. Trigger the DAG in Airflow UI or wait for scheduled run.

## Files of interest
- `dags/etl_mysql_to_s3_redshift_dag.py`: Airflow DAG that orchestrates tasks.
- `scripts/extract_mysql.py`: Connects to MySQL and extracts tables to CSV.
- `scripts/transform_data.py`: Cleans and prepares data.
- `scripts/load_to_s3.py`: Uploads files to S3 using boto3.
- `scripts/load_to_redshift.py`: Executes COPY command to load data to Redshift.
