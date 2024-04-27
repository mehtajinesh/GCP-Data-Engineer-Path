# Modern Data Warehouse

- Enterprise data warehouse should consolidate data from many sources.
- A data lake is just raw data, but an enterprise data warehouse brings the data together and makes it available for querying and data processing.
- The purpose of a data warehouse is not to store data. That's the purpose of a data lake.
- If we have raw data that we want to keep around but not necessarily query, don't bother with cleaning and streamlining it, leave it in a data lake.
- All data in a data warehouse should be available for querying. It's important to ensure that those queries are quick.

## Ideal Properties of Modern Data Warehouse

- We want a single data warehouse that can scale from gigabytes to petabytes of data.
- Data warehouse to be serverless and fully no-ops.
- We don't want to be limited to clusters that we need to maintain, or indexes that we need to fine-tune. Removing these responsibilities will allow data analysts to carry out ad hoc queries faster, which is important because we want the data warehouse to increase the speed at which our business makes decisions.
- Seamlessly plug into whichever visualization or reporting tool our business is most familiar with.
- Able to integrate with an ecosystem of processing tools for building ETL pipelines.
- Capable of constantly refreshing data in the warehouse in order to keep it up to date. We need to be able to stream data into the warehouse and not rely on batch updates.
- Support machine learning without moving the data out of the warehouse.
- Last but not least, in a modern data warehouse, it should be possible to impose enterprise grade security like data exfiltration constraints. It should also be possible to share data and queries with collaborators.
