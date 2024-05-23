# Hadoop on Dataproc

## Key Features

- Low cost:
  - 1 cent per virtual CPU per cluster per hour
  - also possible to include preemptible instances that have lower compute costs
  - pay-per-use model (one-minute-minimum billing period)
- Super-fast:
  - Quick to start, scale and shutdown (each operation takes <90 secs)
- Resizeable clusters:
  - clusters scaled up and down easily with a variety of VM types, disk sizes, etc.
- Open source ecosystem:
  - Use Spark and Hadoop tols and libs
- Integrated:
  - Use other services like Cloud Storage, BigQuery and Cloud Bigtable
- Managed:
  - Easily interact with clusters and Spark/Hadoop jobs without admin support (using SDK, Console, API)
- Versioning:
  - Easy switch between versions
- Highly available:
  - Run cluster with multiple primary nodes and set nodes to restart on failure (by default off)
- Developer tools:
  - Multiple ways to manage cluster (SDK, API, etc)
- Initialization actions:
  - Init cluster with some customization and libs
- Auto/Manual Config:
  - Both ways of config for cluster is possible

## Customzing Clusters

- Use of Preconfigured Optional Components:
  - Hive, Jupyter Notebook, etc
- Initialization Actions:
  - run on all nodes in your dataproc after setup
  - lot of templates available on docs

## Architecture of Cluster

- A Dataproc cluster can contain either preemptible secondary workers or non-preemptible secondary workers, but not both.
- We have a cluster of virtual machines for processing and then persistent disks for storage via HDFS.
- We've also got your manager node VM (or VMs) and a set of worker nodes.
- Worker nodes can also be part of a managed instance group, which is just another way of ensuring that VMs within that group are all of the same template. The advantage is that we can spin up more VMs than we need to automatically resize your cluster based on the demands. Google Cloud recommends a ratio of 60/40 as the maximum between standard VMs and preemptible VMs.
- General practice: should spin the cluster up when we need compute processing for a job and then simply turn them down.

## Why use Cloud Storage instead of HDFS

- The storage would go away too when we turn these clusters down. Best practice to use storage that's off cluster by connecting to other Google Cloud products.
- Eg: Instead of using native HDFS on a cluster, we could simply use a cluster on Cloud Storage via the HDFS connector. Change the prefix for this storage from hdfs// to gs//.
- Hbase off-cluster can be written to Cloud Bigtable.
- Large Analytical Workloads can be written into BigQuery.

## Sequence of Events for create cluster in Dataproc

### Setup

- Creating a cluster.
- Can be done that through
  - Cloud Console,
  - Command line using the gcloud command.
  - Export a YAML file from an existing cluster or create a cluster from a YAML file.
  - From a Terraform configuration,
  - REST API.

### Configure

- The cluster can be set as a single VM, which is usually to keep costs down for development and experimentation.
- Standard is with a single Primary Node, and High Availability has three Primary Nodes.
- We can choose a region and zone, or select a "global region" and allow the service to choose the zone for us.
- The cluster defaults to a Global endpoint, but defining a Regional endpoint may offer increased isolation and in certain cases, lower latency.
- The Primary Node is where the HDFS Namenode runs, as well as the YARN node and job drivers.
- HDFS replication defaults to 2 in Dataproc.
- Cluster properties are run-time values that can be used by configuration files for more dynamic startup options.
- And user labels can be used to tag the cluster for our own solutions or reporting purposes.
- The Primary Node Worker Nodes, and preemptible Worker Nodes, if enabled, have separate VM options, such as vCPU, memory, and storage.
- Preemptible nodes include YARN NodeManager but they do not run HDFS.
- There are a minimum number of worker nodes, the default is 2.
- The maximum number of worker nodes is determined by a quota and the number of SSDs attached to each worker.
- Specify initialization actions, such as initialization scripts that can further customize the worker nodes.
- Metadata can be defined so that the VMs can share state information.

### Optimize

- Preemptible VMs can be used to lower costs. Just remember they can be pulled from service at any time and within 24 hours. So our application might need to be designed for resilience to prevent data loss.
- Custom machine types allow us to specify the balance of Memory and CPU to tune the VM to the load, so we are not wasting resources.
- A custom image can be used to pre-install software so that it takes less time for the customized node to become operational than if we installed the software at boot-time using an initialization script.
- Use a Persistent SSD boot disk for faster cluster start-up.

### Utilize

- Jobs can be submitted through the cloud console, the gcloud command, or the REST API.
- They can also be started by orchestration services such as Dataproc Workflow and Cloud Composer.
- Don't use Hadoop's direct interfaces to submit jobs because the metadata will not be available to Dataproc for job and cluster management, and for security, they are disabled by default.
- By default, jobs are not restartable. However, we can create restartable jobs through the command line or REST API.

### Monitor

- monitor it using Cloud Monitoring.
- Build a custom dashboard with graphs and set up monitoring of alert policies to send emails for example, where we can notify if incidents happen.
- Any details from HDFS, YARN, metrics about a particular job or overall metrics for the cluster like CPU utilization, disk and network usage, can all be monitored and alerted on with Cloud Monitoring.
