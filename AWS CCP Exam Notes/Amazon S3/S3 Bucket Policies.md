- JSON based policies
	- Resources: buckets and objects
	- Effect: Allow / Deny
	- Actions: Set of API to Allow or Deny
	- Principal: The account or user to apply the policy to 
- Use [[S3]] bucket for policy to:
	- Grant public access to the bucket
	- Force objects to be encrypted at upload
	- Grant access to another account (Cross Account)
- Example: Public Access - Use Bucket Policy
	- Enable public access via S3 Bucket Policy
	- IAM user with IAM Policy that allows access to S3 Buckets
- Example: EC2 instance access - Using IAM Roles
	- Create [[EC2]] Instance Role with [[IAM]] permissions that can access S3 Bucket
- Example: Cross-Account Access - Using Bucket Policy
	- IAM User from other AWS account can access S3 Bucket via the S3 Bucket Policy allowing "Cross-Account" access

##### Bucket settings for Block Public Access
- On by default, override previous access methods
- Can be set at the account level