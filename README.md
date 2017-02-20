Session 3
Assignment 5

1. High Availability of Namenode:
The HDFS NameNode High Availability feature enables you to run redundant NameNodes in the same cluster in an Active/Passive configuration with a hot standby. This eliminates the NameNode as a potential Single Point of Failure (SPOF) in an HDFS cluster.
Formerly, if a cluster had a single NameNode, and that machine or process became unavailable, the entire cluster would be unavailable until the NameNode was either restarted or started on a separate machine. 
This situation impacted the total availability of the HDFS cluster in two major ways:
•	In the case of an unplanned event such as a machine crash, the cluster would be unavailable until an operator restarted the NameNode.
•	Planned maintenance events such as software or hardware upgrades on the NameNode machine would result in periods of cluster downtime.
HDFS NameNode HA avoids this by facilitating either a fast failover to the new NameNode during machine crash, or a graceful administrator-initiated failover during planned maintenance.

2. Check Pointing:
A Checkpoint Node was introduced to solve the drawbacks of the NameNode. The changes are just written to edits and not merged to FSImage during the runtime. If the NameNode runs for a while edits gets huge and the next startup will take even longer because more changes have to be applied to the state to determine the last state of the metadata.
The Checkpoint Node fetches periodically FSImage and edits from the NameNode and merges them. The resulting state is called checkpoint. After this is uploads the result to the NameNode.
There was also a similar type of node called “Secondary Node” but it doesn’t have the “upload to NameNode” feature. So the NameNode need to fetch the state from the Secondary NameNode. It also was confusing because the name suggests that the Secondary NameNode takes the request if the NameNode fails which isn’t the case.

3. HDFS Federation:
•	HDFS Federation improves the existing HDFS architecture through a clear separation of namespace and storage, enabling generic block storage layer. 
•	It enables support for multiple namespaces in the cluster to improve scalability and isolation. 
•	Federation also opens up the architecture, expanding the applicability of HDFS cluster to new implementations and use cases.
•	HDFS has two main layers namely,
	Namespace
	Block Storage-Block management and Physical Storage

4. The files that are to be configured for sure while installing a Hadoop cluster:
•	Core-site.xml
•	HDFS-site.xml
•	YARN-site.xml
•	xml
