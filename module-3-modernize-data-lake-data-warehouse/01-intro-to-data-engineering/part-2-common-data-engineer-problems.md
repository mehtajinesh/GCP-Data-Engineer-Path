# Common Problems

## Access the data

- Sample Usecase: We want to compute the customer acquisition cost, how much does it cost in terms of marketing and promotions and discounts to acquire a customer?

- To answer this, We might require data which may be scattered across a variety of marketing products and CRM products
- Challeges
  - Each team has their own data store for their process which may/may not be structured. So integrating them and getting a query run could be a big challenge
  - Also, access to these data stores would be difficult as most department may have default restrictions on communicating the data outside the team.

## Data accuracy and quality not up to the mark

- Need to clean, format and get data ready for insights
- Data lake contains raw data, Data Warehouse contains transformed, clean data
- Data Warehouse: consolidated place to store all the data that is easily joinable and queryable
- Data stored in warehouse is efficient to query.
- Note: Always assume that the data which comes from raw sources are uncleaned and unformatted.

- Sample Usecase: Need to identify the best performing in-store promotion in region X

- To answer this, we need to have data from promotions and stores
- Challenges
  - Some of the stored data might be missing (because people may have used cash)
  - Some transactions might be spread over multiple receipts, hence needs a combine operation (since all the transactions are from one user)
  - We may want to compare the data across the globe with other stores, so need to transform date in UTC
  - Many stores might be storing data in TXT format for promotions which could be difficult to pull

## Availablility of computation resources

- When performing ETL operation, who own the responsibility to perform these operations
- Do we need to have clusters managed by the on-prem resources?
- Problem: If traffic is less, resource wastage, if traffic is more, job takes too much time to process.

## Query performance

- Managing query performance on-prem comes with overhead
  - Installing query engine
  - Constant patch on query engine and updating
  - Managing clusters/reclusters
  - Optimize for concurrent queries and quota/demand
