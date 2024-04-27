# Loading Data

## Batch Loading

- In addition to CSV, you can also use data files with delimiters other than commas by using the field_delimiter flag.
- BigQuery supports loading gzip compressed files. However, loading compressed files isn't as fast as loading uncompressed files.
- For time-sensitive scenarios or scenarios in which transferring uncompressed files to Cloud Storage is bandwidth- or time-constrained, conduct a quick loading test to see which alternative works best. Because load jobs are asynchronous, you don't need to maintain a client connection while the job is being executed.
- BigQuery determines the data schema as follows: If your data is in Avro format, which is self-describing, BigQuery can determine the schema directly.
- If the data is in JSON or CSV format, BigQuery can auto-detect the schema, but manual verification is recommended. You can specify a schema explicitly by passing the schema as an argument to the load job.
- Ongoing load jobs can append to the same table using the same procedure as the initial load, but do not require the schema to be passed with each job.
- If your CSV files always contain a header row that should be ignored after the initial load and table creation, you can use the skip_leading_rows flag to ignore the row.
- BigQuery sets daily limits on the number and size of load jobs that you can perform per project and per table.
- In addition, BigQuery sets limits on the sizes of individual load files and records.
- To automate the process, you can set up Cloud Functions to listen to a Cloud Storage event that is associated with new files arriving in a given bucket and launch a BigQuery load job.
- BigQuery can import data stored in the JSON file format, as long as it is newline delimited. It can also import files in Avro, Parquet, and ORC format. The most common import is with CSV files, which are the bridge between BigQuery and spreadsheets.
- BigQuery can also directly import Firestore and Datastore export files.

## Stream/Periodic Data: BigQuery Data Transfer Service

- the API is mainly used from either Dataproc or Dataflow.
- The BigQuery Data Transfer Service provides connectors and pre-built BigQuery load jobs that perform the transformations necessary to load report data from various services directly into BigQuery.
- A typical Data Warehouse system requires a lot of code for coordination and interfacing.
- You can get BigQuery Data Transfer Service running without coding.
- The core of BigQuery Data Transfer Service is scheduled and automatic transfers of data from wherever it is located (in your data center, on other clouds, in SaaS services) in to BigQuery.
- Transfering the data is only the first part of building a data warehouse. If you were assembling your own system, you would need to stage the data so that it can be cleaned (data quality), and transformed (E-L-T, extract, load, transform), and processed (put into its final and stable form).
- A common issue with Data Warehouse systems is late arriving data.
- For example, a cash register closes late and does not report its daily receipts during the scheduled transfer period.
- To complete the data, you would need to detect that not all of the data was received, and then request the missing data to fill in the gap.
- This is called "data backfill" and it is one of the automatic processes provided by BigQuery Data Transfer Service.
- "Backfilling data" means adding missing past data to make a dataset complete with no gaps and to keep all analytic processes working as expected.
- Use the data transfer service for repeated, periodic, scheduled imports of data directly from Software as a Service systems into tables in BigQuery.
- The BigQuery Data Transfer Service provides connectors, transformation templates, and the scheduling. The connectors establish secure communications with the source service and collect standard data, exports, and reports. This information is transformed within BigQuery. The transformations can be quite complicated, resulting in from 25 to 60 tables. And the transfer can be scheduled to repeat as frequently as once a day.
- The BigQuery Data Transfer Service can also be used to efficiently move data between regions. BigQuery Data Transfer Service runs BigQuery jobs that transform reports from SaaS sources into BigQuery Tables and Views.

## Scheduled Queries

- You can schedule queries to run on a recurring basis.
- Scheduled queries must be written in standard SQL, which can include Data Definition Language and Data Manipulation Language statements.
- The query string and destination table can be parameterized, allowing you to organize query results by date and time.
- By maintaining a complete 7-day history of changes against your tables, BigQuery allows you to query a point-in-time snapshot of your data.
- You can easily revert changes without having to request a recovery from backups.

## Custom Functions

- BigQuery supports user-defined functions, or UDF.
- A UDF enables you to create a function using another SQL expression or an external programming language.
- JavaScript is currently the only external language supported.
- We strongly suggest you use Standard SQL though, because BigQuery can optimize the execution of SQL much better than it can for JavaScript.
- UDFs allow you to extend the built-in SQL functions.
- UDFs take a list of values, which can be ARRAYs or STRUCTs, and return a single value, which can also be an ARRAY or STRUCT.
- UDFs written in JavaScript can include external resources, such as encryption or other libraries.
- Previously, UDFs were temporary functions only. This meant you could only use them for the current query or command-line session.
- When you create a UDF, BigQuery persists it and stores it as an object in your database. What this means is you can share your UDFs with other team members or even publically if you wanted to.
