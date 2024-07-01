# Different Google Cloud Solutions for Databases and Data Warehouse

- For SQL Server, MySQL or PostgresSQL, we can use Cloud SQL (Google's fully managed RDBMS solution)
- Cloud SQL
  - High performance
  - upto 64TB of storage cap
  - 60,000 IOPS
  - 624GB of RAM per instance
  - Autoscaling

## If Cloud SQL is so efficient and so good, why dont we use this for workflow/pipelines rather than data warehouse

- Cloud SQL is optimized for being a database which can handle transactions (writes) [Record - Based Storage (entire record has to be opened on disk)]
- BigQuery (Warehouse) is optimized for being a warehouse which can handle reporting workloads (reads) [Column - Based Storage (entire columns can be fetched out of disk)]

## Usecase for Cloud SQL

- Example: Point of sale terminal at a storefront.
- Each order and product is likely written out as new records in a relational database somewhere.
- This database may store all of the orders received from their website.
- All of the products listed in the catalog or the number of items in their inventory.
- This is so that when an existing order is changed, it can be quickly updated in the database.
- Transactional systems allow for a single row in a database table to be modified in a consistent way.
- They also are built on certain relational database principles like referential integrity to guard against cases like a customer ordering a product that doesn't exist in the product table.

## Overview

![Alt text](./Pipeline-Overview.drawio.svg)
