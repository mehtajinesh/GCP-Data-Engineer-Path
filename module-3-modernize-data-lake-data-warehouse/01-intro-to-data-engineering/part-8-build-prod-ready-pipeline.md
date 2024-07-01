# Common questions for End-to-End pipelines

- How can we ensure pipeline health and data cleanliness
- How do we productionalize these pipelines to minimize maintenance and maximize uptime
- How do we respond and adapt to changing schemas and business needs
- Are we using the latest data engineering tools and best practices

## Simple Answer: Cloud Composer [Apache Airflow]

- For example, when a new CSV file gets dropped into Cloud Storage, we can automatically have that trigger an event that kicks off a data processing workflow and puts that data directly into our data warehouse.
- The power of this tool comes from the fact that Google Cloud big data products and services have API endpoints that we can call.
- A Cloud Composer job can then run every night or every hour and kick off our entire pipeline from raw data to the data lake and into the data warehouse for us.
