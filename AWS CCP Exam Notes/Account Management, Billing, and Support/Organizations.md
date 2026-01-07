- Global Service
- Allows to manage multiple AWS accounts
- The main account is the master account
- Cost Benefits:
	- Consolidated Billing across all accounts - single payment method
	- Pricing benefits from aggregated usage (volume discount for [[EC2]], [[S3]]...)
	- Pooling of Reserved [[EC2]] instances for optimal savings
- API is available to automate AWS account creation
- Restrict Account privileges using Service Control Policies ([[SCP]])

- Can use multi account vs One Account Multi [[VPC]]
- Use tagging standards for billing purposes
- Enable [[CloudTrail]] and send logs to a central [[S3]] account
- Send [[CloudWatch Logs]] to central logging account

- Organize Accounts into Organizational Units (OUs)