# Role of Data Engineer

- Build data pipelines to enable data-driven decisions
  - Batch Pipelines
    - Dataproc or Dataflow
  - Streaming Pipelines
    - Pub/Sub -> Dataflow -> BigQuery

## Why built data pipelines

- Want to get their data intor a place (dashboard/report/ML Model) from where business can make data-driven decisions.
- Data has to be in usable condition for someone to use and make decisions

## Why Data Lake

- Data Lake brings together data from across the enterprise into a single location
- Eg: getting data from RDBS, Spreadsheet, other raw data into one place (data lake)

## How to choose which type of resource to select for Data Lake - Look at answering the following

- Does our data lake resource handle all the types of data we have
  - If we have RDBS then, its better to put data in Cloud SQL
- Can all the data fit into a cloud Storage bucket
- Can it elastically scale to meet the traffic
- Does the resource support horizontal scaling
- Does it support high-throughout ingestion
- Whats the max network bandwidth for the resource
- What fine-grained is the access control on objects
- Do we need to seek within a file

## Options in GCP

- Cloud Storage Bucket
  - Good option for staging all raw data in one place
  - Commonly used for backup and archival
  - Benefit: High availiability, Durable and Performant

## How Data Engineers use Cloud Storage

- Store raw files like CSV, JSON or Avro files.
- Load them/query from them in BigQuery as Data Warehouse
