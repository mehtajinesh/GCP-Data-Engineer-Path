# Optimizing Dataproc Storage

## When to use Local HDFS

- good option if our jobs require a lot of metadata operations, like modify data/ rename in thousands of partitions and directories, and each file size is relatively small.
- renaming a directory is an expensive operation in Cloud Storage
- use the append operation on HDFS files, involve heavy IO (especially sensitive to latency)

## Recommendation for Cloud Storage

- Initial and final source of data in a big data pipeline.
- retrieves the initial data from Cloud Storage, final job writes its results to Cloud Storage
- Using Dataproc with Cloud storage allows us to reduce the disk requirements and save costs
- Note: Even if you store all of our data in Cloud Storage, our Dataproc cluster needs HDFS for certain operations, such as storing control and recovery files, or aggregating logs.

## Optimizing Local HDFS

- Decrease the total size of the local HDFS by decreasing the size of primary persistent disks for the primary and workers.
- Increase the total size of the local HDFS by increasing the size of the primary persistent disk for workers.
- Attach up to eight SSDs to each worker and use these disks for the HDFS. (use the HDFS for IO intensive workloads)
- Use SSD persistent disks for our primary or workers as a primary disk.

## Different Storage Options for Different Jobs

- Cloud Storage is the primary way to store unstructured data in Google Cloud
- We can use Cloud Bigtable to store large amounts of sparse data. Cloud Bigtable is an HBase compliant API that offers low latency and high scalability to adapt to our jobs.
- For data warehousing, we can use BigQuery.

## Why not to use HDFS on Google Cloud

- Keeping our data in a persistent HDFS cluster using Dataproc is more expensive than storing our data in Cloud storage.
- Keeping data in an HDFS cluster also limits our ability to use our data with other Google Cloud products.
- Augmenting or replacing some of our open source based tools with other related Google Cloud services can be more efficient or economical for particular use cases.
- Using a single persistent Dataproc cluster for our jobs is more difficult to manage than shifting to targeted clusters that serve individual jobs or job areas.

## Overall new Idea: ephemeral model

- The most cost-effective and flexible way to migrate your Hadoop system to Google Cloud is to shift away from thinking in terms of large, multi-purpose persistent clusters, and instead think about small, short-lived clusters that are designed to run specific jobs. We store your data in Cloud storage to support multiple temporary processing clusters.

## Schedule a Delete of Cluster

- If you have efficient utilization, don't pay for resources that you don't use, employ scheduled deletion.
- A fixed amount of time after the cluster enters an idle state, you can automatically set a timer, you can give it a timestamp, and the count starts immediately once the expiration has been set.
- You can set a duration, the time in seconds to wait before automatically turning down the cluster.
- You can range from 10 minutes as a minimum to 14 days as a maximum at a granularity of one second.