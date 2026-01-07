- Fully managed highly available with replication across 3 AZ
- Part of NoSQL database - not a relational database
- Scales to massive workloads, distributed "serverless" database
- Millions of requests per seconds, trillions of rows, 100s of TBs of storage
- Fast and consistent performance
- Single-digit ms latency - low latency retrieval
- Integrated with [[IAM]] for security, auth and administration
- Low cost and auto scaling capabilities
- Standard and Infrequent Access Table Class

##### Type of data
- DynamoDB is a key/value database

###### DynamoDB Accelerator - [[DAX]]
- Fully Managed in-memory cache for DynamoDB
- 10x performance improvement - single digit ms latency to microseconds latency - when accessing your DynamoDB tables
- Only for DynamoDB
- [[ElastiCache]] can be used for other databases while [[DAX]] is only for DynamoDB