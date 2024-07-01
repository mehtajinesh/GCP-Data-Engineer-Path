# Data Lake and Warehouses

- the raw data is by itself not very useful.
- raw data gets replicated and stored in a data lake.
- In order to make that data usable, we will use Extract Transform Load or ETL pipelines to make the data usable and store this more usable data in a data warehouse

## Questions on Warehouse

- Data warehouse is going to definitely serve as a sink
- Will it be fed by a batch pipeline or by a streaming pipeline?
- Does the warehouse need to be accurate up to the minute? Or is it enough to load data into it once a day or once a week?
- Will the data warehouse scale to meet my needs?
- Many cluster based data warehouses will set per cluster concurrent query limits. Will those query limits cause a problem? Will the cluster size be large enough to store and traverse our data?
- How is the data organized, cataloged and access controlled?
- Will we be able to share access to the data to all our stakeholders? What happens if they want to query the data?
- Who will pay for the querying?
- Is the warehouse designed for performance?
- Again, carefully consider concurrent query performance and whether that performance comes out of the box, or whether we need to go around creating indexes and tuning the data warehouse.
- Finally, what level of maintenance is required by our engineering team?

## Answer to above questions: BigQuery [getting data into BigQuery by running ETL pipelines]

- BigQuery is a modern data warehouse that changes the conventional mode of data warehousing
- BigQuery provides mechanisms for automated data transfer, empowers business applications using technology that teams already know and use, so everyone has access to data insights
- Create read-only shared data sources that both internal and external users can query, and make query results accessible for anyone through user-friendly tools such as Looker, Google Sheets, Tableau, or Google Data Studio.
- BigQuery lays the foundation for AI, it's possible to train TensorFlow and Google Cloud Machine Learning models directly with datasets stored in BigQuery, and BigQuery ML can be used to build and train machine learning models with simple SQL
- BigQuery GIS, which allows organizations to analyze geographic data in BigQuery essential to many critical business decisions that revolve around location data.
- BigQuery also allows organizations to analyze business events real time as they unfold by automatically ingesting data and making it immediately available to query in their data warehouse
- Ingest up to 100,000 rows of data per second and for petabytes of data to be queried at lightning fast speeds.
- BigQuery also simplifies data operations through the use of identity and access management to control user access to resources, creating roles and groups and assigning permissions for running jobs and queries in a project and also providing automatic data backup and replications.

## BiqQuery as Query Engine

- use BigQuery to directly query database data in Cloud SQL, that is, managed relational databases like Postgres SQL and MySQL.
- use BigQuery to directly query files on Cloud Storage as long as these files are in formats like CSV or Parquet
- we can leave our data in place and still join it against other data in the data warehouse
