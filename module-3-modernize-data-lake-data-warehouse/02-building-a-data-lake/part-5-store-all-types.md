# Consideration for storing data

- Data can be structured or unstructured

- Unstructured
  - Cloud Storage

- Structured
  - Transactional Workload
    - SQL
      - Cloud SQL
      - Cloud Spanner
    - NoSQL
      - Firestore
  - Data Analytics Workload
    - Cloud Bigtable (millisecond latancy)
    - BigQuery (second latency)

## Transactional VS Analytical

- Transactional Workload
  - Require fast inserts and updates
  - Maintain a snapshot, current state of the system
  - Affect only few records
  - Online Transaction Processing (OLTP)
  - Eg: Updating a balance for a worker
  - Write Heavy, constantly updating Operation Systems, hence the snapshot
  - For example, a retailer’s catalog data will require updating every time the retailer adds a new item or changes the price. The inventory data will need to be updated every time the retailer sells an item. This is because the catalog and inventory systems have to maintain an up-to-the-moment snapshot of the business.

- Analytical Workload
  - Read the entire dataset and used for planning or decision making
  - Data comes from OLTP but often consolidated from many OLTP
  - Eg: Generating a report which says a list of users who have done more than X transaction per day
  - Online Analytical Processing (OLAP)
  - Periodically populated from Operation Systems (Set of all the DBs like Inventory, Catalog, etc)
  - For example, We could use this once a day to generate a report of items in our catalog whose sales are increasing, but whose inventory levels are low. Such a report will have to read a bunch of data, but not have to write much.

## Why can't we directly use BigQuery for loading data in EL

- On Google Cloud, the data warehouse tends to be BigQuery.
- There is a limit to the size of the data that you can directly load to BigQuery.
- This is because your network might be a bottleneck.
- Rather than load the data directly into BigQuery, it can be much more convenient to first load it to Cloud Storage and load from Cloud Storage to BigQuery.
- Loading from Cloud Storage will also be faster because of the high throughput it offers.

## Choices

- We can use Cloud SQL (Default) for transactional workloads for single region
- Use Cloud Spanner for distributed databases and apps running across different geographic regions
- True Time capability of Spanner is useful if we have a globally distributed database (see updates from apps running globally)
- Another reason you might choose Spanner is if your database is too big to fit into a single Cloud SQL instance.
- We can use BigQuery (Default) for analytical workloads.
- If we need high-throughput inserts more than millions of rows per sec, switch to Cloud Bigtable else use BigQuery as it is cost-effective.
