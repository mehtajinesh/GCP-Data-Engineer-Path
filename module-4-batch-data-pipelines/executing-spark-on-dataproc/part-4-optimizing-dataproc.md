# Optimizing Dataproc

- Where is our data and where is our cluster?
  - Make sure that your data's region and your cluster zone are physically close in distance.
  - We can use Dataproc Auto Zone feature if not sure
  - Make sure Cloud Storage and Dataproc in same zone
- Is Network traffic being funneled?
  - Dont have any network rules that funnel Cloud storage traffic through a small number of VPN gateways
  - Avoid network bottlenecks
- Number of Input files and Hadoop Partition
  - keep it less than around 10,000 input files
  - If needed, merge them into larger files and increase hadoop block size if needed
- Size of persistent disk
  - Make sure that you haven't selected persistent disk for larger applications (scales linearly and creates problems)
- Allocate enough VMs on cluster
  - run prototypes and benchmarking to identify an ideal cluster size and VM allocation config
  