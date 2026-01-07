#### Naming Convention
- Example: m5.2xlarge
- m: instance class
- 5: generation (AWS improves them over time)
- 2xlarge: size within the instance class

##### General Purpose
- Great for a diversity of workloads such as web servers or code repositiories
- Balance between:
	- Compute 
	- Memory
	- Networking
- In the course, we will be using the t3.micro which is a General Purpose EC2 instance
##### Compute Optimized
- Great for compute-intensive tasks that require high performance processors (c name):
	- Batch processing workloads
	- Media transcoding
	- High performance web servers
	- High performance computing (HPC)
	- Scientific modeling and machine learning
	- Dedicated gaming servers

##### Memory Optimized (R series, X1, Z1)
- Fast performance for workloads that process large data sets in memory
- Use cases:
	- High performance, relational/non-relational databases
	- Distributed web scale cache stores
	- In-memory databases optimized for Business Intelligence ([[BI]])
	- Applications performing real-time processing of big unstructured data
##### Storage Optimized
- Great for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage
- Use cases:
	- High frequency online transaction processing (OLTP) systems
	- Relational and NoSQL databases
	- Cache for in-memory databases (for example, Redis)
	- Data warehousing applications
	- Distributed file systems
