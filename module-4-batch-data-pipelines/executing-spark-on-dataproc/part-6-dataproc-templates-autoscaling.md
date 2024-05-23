# Templates in Dataproc

- The Dataproc Workflow Template is a YAML file that is processed through a Directed Acyclic Graph or DAG.
- It can create a new cluster, select from an existing cluster, submit jobs, hold jobs for submission until dependencies can complete, and it can delete a cluster when the job is done.
- It’s available through the gcloud command and the REST API. You can view existing workflow templates and instantiated workflows through the Google Cloud console as well.
- The Workflow Template becomes active when it is instantiated into the DAG.
- The Template can be submitted multiple times with different parameter values.
- You can also write a template inline in a gcloud command, and you can list workflows and workflow metadata to help diagnose issues.
- Eg:
  - Setup scripts for installing
  - Create cluster
  - Steps in job
  - Submit workflow template

## Scaling in Dataproc

- Dataproc autoscaling provides clusters that size themselves to the needs of the enterprise. 
- Key features include: Jobs are “fire and forget”, There’s no need to manually intervene when a cluster is over or under capacity, You can choose between standard and preemptible workers, and You can save resources such as quota and cost at any point in time Autoscaling policies provide fine-grained control.
- Dataproc autoscaling provides flexible capacity for more efficient utilization, making scaling decisions based on Hadoop YARN Metrics.
- It doesn’t support Spark Structured Streaming, a streaming service built on top of Spark SQL.
- It’s also not designed to scale to zero. So it’s not the best for sparsely utilized or idle clusters.
- In these cases it’s equally fast to terminate a cluster that’s idle and create a new cluster when it’s needed. For that purpose you would look at Dataproc Workflows or Cloud Composer, and Cluster Scheduled Deletion.
- One of the things that you want to consider when working with autoscaling is setting the initial workers. The number of initial workers is set from Worker Nodes, Nodes Minimum. Setting this value ensures that the cluster comes up to basic capacity faster than if you let autoscaling handle it.
- The primary minimum number of workers may be the same as the cluster nodes minimum.
- After the rescaling action, there is a cooldown period to let things settle before autoscaling evaluation occurs again.
- The cooldown period reduces the chances that the cluster will start and terminate nodes at the same time.