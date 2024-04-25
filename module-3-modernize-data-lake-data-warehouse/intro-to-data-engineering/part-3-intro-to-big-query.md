# BigQuery - Serverless Data Warehouse

- Google Cloud's petabyte scale serverless data warehouse, no need to manage clusters, just focus on insights
- Has a set of datasets for the organization.
- Each dataset is tied to a Google Cloud project.
- Input can come from Cloud Storage/Google Drive/Cloud Bigtable
- IAM is used to manage permissions (replaces SQL Grant and Revoke Statements)
- Allocates storage and query resources dynamically based on our usage patterns
- Storage resources are allocated as we consume them and de-allocated as we remove data or drop tables
- Query resources are allocated according to query type and complexity
- Each query uses some number of slots, which are units of computation that comprise a certain amount of CPU and RAM
