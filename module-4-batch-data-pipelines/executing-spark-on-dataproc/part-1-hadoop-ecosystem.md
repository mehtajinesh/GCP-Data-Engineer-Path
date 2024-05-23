# Hadoop Overview

## What is Hadoop

- Database design came from a time when storage was relatively cheap and processing was expensive, so it made sense to copy the data from its storage location to the processor to perform data processing, then the result will be copied back to storage.
- The idea behind Hadoop is to create a cluster of computers and leverage distributed processing.
- HDFS, the Hadoop Distributed File System, stored the data on the machines in the cluster and MapReduce provided distributed processing of the data.
- A whole ecosystem of Hadoop related software grew up around Hadoop, including Hive, Pig and Spark.
- Organizations use Hadoop for on-premises big data workloads. They make use of a range of applications that run on Hadoop clusters, such as Presto, but a lot of customers use Spark.
- Apache Hadoop is an open source software project that maintains the framework for distributed processing of large datasets across clusters of computers using simple programming models.
01:16
HDFS is the main file system Hadoop uses for distributing work to nodes on the cluster.

## Spark Overview

- Apache Spark is an open source software project that provides a high performance analytics engine for processing batch and streaming data.
- Spark can be up to 100 times faster than equivalent Hadoop jobs because it leverages in memory processing.

## Problems with On-premises Hadoop clusters

- No seperation between storage and compute resources
- Hard to scale fast (only possible to add more physical servers)
- Capacity limits

## Solution: Dataproc

- Built-in support for Hadoop
- Managed hardware and configuration
- Simplified version and management
- Flexible job configuration
- Support for Apache Spark (Python, ML Libs, etc)
