# Shortcoming of ELT

## Eg: Translate Spanish to English

- Requires calling external API, cant be done directly in SQL
- Needs programming outside of BigQuery

## Eg: Customer Action Pattern Detection

- Difficult to do it with Windowed aggregations, rather use programming logic

## When to use ETL

- When the transformations cannot be expressed in SQL or are too complex to do in SQL
- Transform the data before loading in BQ
- Also, when we want data loading to happen continously (streaming)

### One Tool to do ETL: Dataflow

- Usecase:
  - Extract data from Pub/Sub, Cloud Storage, Cloud Spanner, Cloud SQL
  - Transform the data using Dataflow
  - Load the data into BigQuery
- Dataflow supports streaming
- Another Usecase: We want to integrate it with CI/CD process and perform unit testing on all components

## Other Tools for ETL in Google Cloud

- Dataflow
  - Used for complex pipelines
  - fully managed service
  - serverless data processing based on Apache Beam
  - Supports both batch and streaming pipelines
- Dataproc
  - Used for complex pipelines
  - Uses Hadoop, needs expertise
- Cloud Data Fusion
  - simple GUI for ETL pipelines
  - deploy at scale to Dataproc clusters
