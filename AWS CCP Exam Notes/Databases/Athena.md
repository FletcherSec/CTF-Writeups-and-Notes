- **ALWAYS** Serverless query service to perform analytics against [[S3]] objects
- Uses standard SQL language to query the files
- Supports CSV, JSON, ORC, Avro, and Parquet (Built on Presto)
- Price is $5 per TB of data scanned
	- Use compressed or columnar data for cost-saving (less scan)
- Use cases: Business intelligence / analytics/ reporting, analyze and query VPC Flow Logs, ELB logs, CloudTrail trails, etc.

##### ==Exam Tip: Analyze data in [[S3]] using serverless SQL, use [[Athena]]==
