# EL VS ETL VS ELT

## EL

- imported as is into a system.

### When to use EL

- only if the data is already clean and correct
- Eg: log files in Cloud Storage, Extract data from files on Cloud Storage and load it into BigQuery's native storage (Using REST API call and trigger from pipelines using Cloud Composer/Cloud Functions)

## ELT

- allows raw data to be loaded directly into the target and transformed whenever it is needed
- Eg: We might provide access to the raw data through a view that determines whether the user wants all transactions or only reconciled ones.

### When to use ELT

- when we don't know what kind of transformations are needed to make the data usable.
- Eg: upload  a new image, invoke the Vision API and back comes a long JSON message about all kinds of things in the image, text in the image, whether there's a landmark, a logo, what objects. What will an analyst need in the future? We don't know, so we store the raw JSON as is. Later, if someone wants to count the number of times a specific company's logos are in this set of images, they can extract logos from the JSON and then count them.

## ETL

- data integration process in which transformation takes place in an intermediate service before it is loaded into the target
- Eg: data might be transformed in Dataflow before being loaded into BigQuery
