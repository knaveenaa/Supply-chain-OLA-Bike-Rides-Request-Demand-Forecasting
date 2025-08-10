# OLA Ride Demand Forecasting

This project provides a scalable, production-ready pipeline for forecasting ride demand for OLA Bikes, leveraging both local and AWS cloud-based workflows. It is designed to handle millions of records efficiently and supports both batch and real-time inference.

## Project Overview
- **Goal:** Predict ride request demand for OLA Bikes at a fine-grained spatiotemporal level.
- **Scale:** Processes 8M+ records using distributed and modular data pipelines.
- **Cloud Native:** Integrates AWS Glue (Spark), SageMaker, and S3 for scalable ETL, model training, and artifact storage.
- **Local Friendly:** All code and notebooks are runnable on a local machine for development and experimentation.

## Key Features
- **Big Data Processing:** Distributed ETL and feature engineering using AWS Glue and Spark.
- **Model Training:** XGBoost and other regressors, with advanced time-series features (lags, rolling windows, clustering).
- **Modular Code:** Reusable Python modules for each pipeline stage, following best practices.
- **Real-Time & Batch Inference:** FastAPI microservice for real-time predictions; batch pipelines for large-scale scoring.
- **Cloud Storage:** All intermediate data and models are versioned and stored in S3.
- **Notebooks:** Jupyter/SageMaker notebooks for EDA, feature engineering, and model evaluation.

## Directory Structure
- `Ipython_Notebooks/` — Jupyter notebooks for data cleaning, analysis, feature engineering, model training, and prediction.
- `AWS/` - This module helps to run and test in the cloud services here AWS sagemaker is used.
- `modular_code/` — Modular Python code for ETL, feature engineering, model training, and inference.
- `data/` — Sample and intermediate datasets (for local use).
- `venv/` — Python virtual environment for dependency management.
- `requirements.txt` — All required Python packages.
- `Solution+Methodology.pdf` — Detailed solution approach and methodology.

## AWS Workflow
1. **Data Ingestion:** Fetch raw and intermediate data from S3.
2. **ETL & Feature Engineering:** Use AWS Glue (Spark) for distributed processing of large datasets.
3. **Model Training:** Train models in SageMaker notebooks or locally; save models to S3.
4. **Inference:** Deploy models as FastAPI microservices (real-time) or run batch predictions, storing results in S3.

## Local Workflow
1. **Setup:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```
2. **Run Notebooks:**
   Open and execute notebooks in `Ipython_Notebooks/` for EDA, feature engineering, and model training.
3. **Use Modular Code:**
   Import and use modules from `modular_code/` for custom pipelines or API deployment.

## Example API Usage
A FastAPI endpoint is provided for real-time inference. Example request:
```bash
curl -X POST "http://localhost:8000/predict" -H "Content-Type: application/json" -d '{"pickup_cluster": 1, "mins": 0, "hour": 12, "month": 5, "quarter": 2, "dayofweek": 3}'
```

## Solution Methodology
See `Solution+Methodology.pdf` for a comprehensive description of:
- Data pipeline and architecture
- Feature engineering and clustering
- Model selection and evaluation
- Cloud and local deployment strategies

## Requirements
See `requirements.txt` for all dependencies.
