# Why Cloud Storage instead on HDFS

- Network speeds were slow originally. That's why we kept data as close as possible to the processor.
- Now, with petabit networking, we can treat storage and compute independently and move traffic quickly over the network.
- Optimization 1:
  - HDFS in the Cloud just by lifting and shifting our Hadoop workloads to Dataproc
  - requires no code changes
  - but a subpar solution
- Problems with Optimization 1
  - HDFS works on the clusters with block size, the data locality and the replication of the data in HDFS.
  - For block size in HDFS, we're tying the performance of input and output to the actual hardware the server is running on.
  - Also, If we run out of persistent disk space on our cluster, we will need to resize even if we don't need the extra compute power.
  - In order for HDFS to be highly available, it replicates three copies of each block out to storage. It would be better to have a storage solution that's separately managed from the constraints of our cluster.
- Optimization 2:
  - Use Cloud Storage and network bandwidth
  - Jupyter networking fabric within a Google data center delivers over one petabit per second of bandwidth
  - With petabit bisectional bandwidth, the communication is so fast that it no longer makes sense to transfer files and store them locally
  - Inside of a Google data center, the internal name for the massively distributed storage layer is called Colossus. Under the network inside the data center is Jupyter.

## Why use Cloud Storage

- With Cloud Storage as the backend, we can treat clusters themselves as ephemeral resources, which allows us not to pay for compute capacity when we're not running any jobs.
- Also, Cloud Storage is its own completely scalable and durable storage service, which is connected to many other Google Cloud projects.
- Cloud storage could be a drop-in replacement for our HDFS backend for Hadoop, the rest of our code would just work.
- Also, we can use the Cloud storage connector manually on your non-Cloud Hadoop clusters if we didn't want to migrate your entire cluster to the Cloud yet.
- With HDFS, we must over-provision for current data and for data we might have, and we must use persistent disks throughout.
- With Cloud Storage however, we pay for exactly what we need when we use it.
- Cloud Storage is optimized for large bulk parallel operations.
- It has very high throughput, but it has significant latency.
- If we have large jobs that are running lots of tiny little blocks, we may be better off with HDFS.
- Additionally, we want to avoid iterating sequentially over many nested directories in a single job.
- Using Cloud Storage instead of HDFS provides some key benefits due to the distributed service including eliminating bottlenecks and single points of failure.

## When not to choose Cloud Storage

- Cloud Storage is at its core an object store, it only simulates a file directory. So directory renames in HDFS are not the same as they are in Cloud Storage, but new objects store oriented output committers mitigate this as we see here. Disk CP is a key tool for moving data.
- In general, we want to use a push-based model for any data that we know we will need while pull-based may be a useful model if there is a lot of data that we might not ever need to migrate.