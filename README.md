## AWS-Triggered JSON Flattening & ETL Pipeline

This repository demonstrates a robust Python-based ETL (Extract, Transform, Load) pipeline designed to handle semi-structured, deeply nested JSON data. This workflow simulates a serverless data engineering architecture typically found in modern cloud environments like AWS.

## 📊 Project Overview

- In modern data lakes, information arriving from sources like AWS S3 is often hierarchical. This project provides a production-ready logic to:
- Simulate Serverless Triggers: Parse AWS Lambda event objects to extract S3 bucket names and object keys.
- Complex Schema Flattening: Transform multi-level JSON (Customer objects and nested Product lists) into a tabular format.
- Data Lake Optimization: Prepare semi-structured data for high-performance querying in AWS Athena or cataloging in AWS Glue.

## 🛠️ Tech Stack & Cloud Ecosystem

- Language: Python
- Data Libraries: pandas, json
- Cloud Context (Simulated):

a. AWS S3: The landing zone for raw orders_etl.json files.

b. AWS Lambda: The compute engine triggered by S3 events to run this flattening logic.

c. AWS Glue: Ideal next-step for schema discovery and metadata cataloging.

d. AWS Athena: The target analytical tool for querying the resulting flattened data using SQL.

## 📈 ETL Workflow

1. Extraction (S3 Event Parsing)

The pipeline begins by interpreting an AWS S3 event notification. It programmatically identifies the file location:

<img width="691" height="144" alt="Screenshot 2026-02-02 at 14 23 48" src="https://github.com/user-attachments/assets/1b9f9bd3-882f-4732-971a-8748b27936fd" />

2. Transformation (Hierarchical Mapping)

The transformation logic navigates through three levels of nesting:

- Root Level: Order metadata (order_id, order_date).
- Nested Object: customer profile details.
- Nested Array: A list of products within each order.

3. Loading (Flattening for Analytics)

The script "explodes" the product arrays. This ensures that the data is normalized—where each product is a unique row—making it ready for ingestion into a relational database or a Glue Data Catalog.

## 📁 Project Structure

- flatten_data.ipynb: Main execution notebook containing the ETL logic and AWS event simulation.
- orders_etl.json: Sample input file representing raw semi-structured data.

## 💻 Production Logic Snippet

The following logic demonstrates how the pipeline iterates through nested structures to build a structured dataset:

<img width="621" height="352" alt="Screenshot 2026-02-02 at 14 25 33" src="https://github.com/user-attachments/assets/7b7c83ef-5b66-4154-9d66-b779e84ce5f6" />

## 🚀 Deployment & Usage

Clone the repository and ensure orders_etl.json is in the root directory.

## Install Dependencies:


- pip install pandas
- Run the Notebook: Open flatten_data.ipynb to view the step-by-step transformation from a raw S3-style JSON to a clean, query-ready DataFrame.

