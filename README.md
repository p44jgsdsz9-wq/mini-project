# Mini Project 15 – Data Cleaning Pipeline

This project implements a complete data cleaning pipeline for the dataset **day15_real_dataset_large.csv**. 
The goal is to prepare raw data for analysis and machine learning by ensuring correct data types, handling missing values,
reducing the impact of extreme values, standardizing text fields, and making timestamps timezone-aware. First, the dataset is loaded using pandas.
A dedicated function `clean_data_project()` is created to keep all cleaning steps organized and reusable.
The columns `age` and `income` are safely converted to numeric using `errors="coerce"` so invalid values become NaN, and `signup_time` is converted to datetime with invalid entries converted to NaT.
For missing value handling, indicator columns (`age_missing` and `income_missing`) are created to preserve information about originally missing data. Missing values in `age` and `income` are filled
using the median to reduce sensitivity to outliers. Additionally, income is capped at the 99th percentile using clipping (Winsorization) to limit the influence of extreme high values without removing records.
The `city` column is cleaned by converting to string, stripping whitespace, and transforming to lowercase to prevent duplicate categories caused by formatting inconsistencies. 
The `signup_time` column is localized to UTC to ensure consistent and timezone-aware timestamps for future time-based analysis. After cleaning, the dataset is validated using `.info()`, `.describe()`, value counts,
timezone checks, and missing value summaries. Finally, the cleaned dataset is saved as `real_dataset_clean.csv`. This pipeline results in a structured, consistent, and model-ready dataset suitable 
for downstream analyticsand predictive modeling tasks.
