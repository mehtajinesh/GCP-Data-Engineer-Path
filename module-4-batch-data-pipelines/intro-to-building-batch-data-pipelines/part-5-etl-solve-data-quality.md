# ETL to Solve Data Quality Issues

- Recommended to use Dataflow -> BigQuery

## Exceptions to Dataflow -> BigQuery

- Low latency (< 100 millisecond), High Throughput ( > 1 mil rows per second)
  - For both above, we need to do Dataflow -> BigTable
- Use Spark infra/knowledge
  - Use Dataproc
- Create Visual Pipeline without coding expertise
  - Use Data Fusion

## Dataproc Overview

- Managed service for batch processing, querying, streaming and ML
- service for Hadoop workloads, quite cost effective
- removes low level tasks (auto-scaling)

## Cloud Data Fusion Overview

- Managed service, cloud-native, enterprise data integration service for quick build data pipelines
- Use: populate data warehouse, transform and clean data
- Recommended for non-prog people
- Also, API available for automating using scripts

## Concept of Lineage

- Where the data came from, what processes it has been through, and what condition it is in
- If we have the lineage, we know for what kinds of uses the data is suited.
- If we find the data gives odd results, we can check the lineage to find out if there is a cause that can be corrected.
- Lineage also helps with trust and regulatory compliance.

## Label and Use of Data Catalog

- A label is a key-value pair that helps us organize our resources.
- In BigQuery we can attach labels to Datasets, Tables, and Views.
- Labels are useful for managing complex resources because we can filter them based on their labels.
- We can also use this for Cloud Billing.

### Data Catalog

- Data Catalog is a fully managed and highly scalable data discovery and metadata management service.
- It is serverless and requires no infrastructure to set up or manage.
- It provides access-level controls and honors source A-C-Ls for read, write, and search for the data assets; giving us enterprise-grade access control.
- Think of Data Catalog as a metadata-as-a-service.
- It provides metadata management service for cataloging data assets via custom APIs and the UI, thereby providing a unified view of data wherever it is.
- It supports schematized tags (e.g., E-num, Bool, DateTime) and not just simple text tags — providing organizations rich and organized business metadata.
- It offers unified data discovery of all data assets, spread across multiple projects and systems.
- It comes with a simple and easy-to-use search UI to quickly and easily find data assets; powered by the same Google search technology that supports Gmail and Drive.
- As a central catalog, it provides a flexible and powerful cataloging system for capturing both technical metadata (automatically) as well as business metadata (tags) in a structured format.
- One of the great things about the data discovery is that it integrates with the Cloud Data Loss Prevention API.
- We can use it to discover and classify sensitive data, providing intelligence and helping to simplify the process of governing our data.
- Data Catalog empowers users to annotate business metadata in a collaborative manner and provides the foundation for data governance.
- Specifically, Data Catalog makes all the metadata about our datasets available to search for our users, regardless of where the data are stored.
- Using Data Catalog, we can group datasets together with tags, flag certain columns as containing sensitive data, etc.
- If we have many different datasets with many different tables — to which different users have different access levels — the Data Catalog provides a single unified user experience for discovering those datasets quickly.
