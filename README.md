# Goodreads Data Lakehouse Project (ID: 60300294)

This is the lab3 what we have to do in Azure Cloud for course in UDST University.

Course Name: Cloud Computing (DSAI 3202)

## Objects of Lab3:
- build a complete **data lakehouse pipeline** on **Azure Databricks** 
- Transforming raw Goodreads data into a cureated and gold dataset.
- do the layers of:
  - Bronze layer (Raw ingestion)
  - Silver layer (Processed/cleaned data)
  - Gold layer (Final analytics-ready data)

## Project Overview:

The pipeline extracts, cleans, and enriches Goodreads book review data using **PySpark** on Databricks.  
Data is stored in **Azure Data Lake Storage Gen2 (ADLS)** and organized into multi-layer zones:

| Layer | Description | Example Path |
|--------|--------------|--------------|
| **Raw** | Original JSON/CSV files from source | `/raw/books/`, `/raw/authors/`, `/raw/reviews/` |
| **Silver (Processed)** | Cleaned and verified parquet data | `/processed/books/`, `/processed/authors/`, `/processed/reviews/` |
| **Gold** | Final curated & feature-engineered tables ready for analytics | `/gold/curated_reviews/`, `/gold/features_v1/` |


## Step in Pipeline

| Step | Description |
|------|--------------|
| **1. Load Silver Data** | Load processed parquet files for books, authors, and reviews. |
| **2. Data Quality Checks** | Count nulls, empty texts, and duplicates. |
| **3. Data Cleaning** | Remove missing keys, trim strings, standardize language, fix malformed characters. |
| **4. Filter Short Reviews** | Drop reviews shorter than 10 characters. |
| **5. Replace Missing Values** | Fill `language` column nulls with `'unknown'`. |
| **6. Feature Engineering** | Create new features like `review_len_words`. |
| **7. Save Gold Table** | Persist final data as Delta table: `default.features_v1`. |
| **8. Sample Export** | Export 100-row samples (for GitHub) from curated and gold datasets. |

## Sample Data Included
i have create Small sample for both `curated_reviews` and `features_v1`

output/

├── sample_curated_data.csv # 100 rows from curated_reviews

└── features_v1_sample.csv # 100 rows from final gold table
