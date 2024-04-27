# Data Storage Options

- Cloud SQL (RDBMS)
- Cloud Spanner (RDBMS)
- Cloud Storage
- Firestore (NoSQL) [High throughput streaming]
- Cloud Bigtable (NoSQL) [High throughput streaming]

## How to decide which option

- Where our data is right now
- How big our data is
- Where does it go from here
- How much transformation is needed
    **Note: In Arch Diagram, generally, the ending point for the data is called a data sync [Example: Common data sync after data lake is data warehouse]**

## Method to load data

- Depends on how much transformation is needed and when it is needed

### Patterns

- Extract and Load (EL)
  - Data is readily available to ingest in the cloud product we want to store it in
  - Example: Data in Avro format -> store into bigquery. Simply use BigQuery to load Avro files
  - EL refers to when data can be imported as-is into a system
  - Source and Destination could have same schema
    **Note: BigQuery serves with a unique feature of performing federated query [Supported : Avro, ORC, Parquet]**

- Extract Load and Transform (ELT)
  - When the data loaded into the cloud product isn't in the final format we want it in.
  - We may want to clean it up, or maybe you want to transform the data in some way. (eg. data needs to be corrected).
  - Extract from our on-premise system, load into the cloud product and then do the transformation.
  - Do this when the amount of transformation that's needed is not very high and the transformation will not greatly reduce the amount of data that we have.
  - ELT allows raw data to be loaded directly into the target and transformed there.
  - For example, in BigQuery, we could use SQL to transform the data and write a new table

- Extract Transform and Load (ETL)
  - extract the data, apply a bunch of processing to it and then load it into the cloud product
  - ETL is a data integration process in which transformation takes place in an intermediate service before it is loaded into the target
  - pick when this transformation is essential, or if this transformation greatly reduces the data size
  - By transforming the data before loading it into the cloud, we might be able to greatly reduce the network bandwidth
  - Another eg: data in some binary proprietary format and we need to convert it before loading
  - For example, the data might be transformed in a data pipeline like data flow before being loaded into BigQuery.
  