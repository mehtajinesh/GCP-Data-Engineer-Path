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
  - Write Heavy Operation Systems

- Analytical Workload
  - Read the entire dataset and used for planning or decision making
  - Data comes from OLTP but often consolidated from many OLTP
  - Eg: Generating a report which says a list of users who have done more than X transaction per day
  - Online Analytical Processing (OLAP)
  - Periodically populated from Operation Systems

## Choices

- We can use Cloud SQL (Default) for transactional workloads for single region and database not big
- Use Cloud Spanner for distributed databases and apps running across different geographic regions
- True Time capability of Spanner is useful if we have a globally distributed database (see updates from apps running globally)
- We can use BigQuery (Default) for analytical workloads.
- If we need high-throughput inserts more than 1 mil rows per sec, switch to Cloud Bigtable else use BigQuery as it is cost-effective.
