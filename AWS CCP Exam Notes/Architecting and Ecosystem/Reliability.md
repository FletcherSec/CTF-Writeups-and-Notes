- Pillar 3 of [[Well Architected Framework]]
- Ability of a system to recover from infrastructure or service disruptions, dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconfigurations or transient network issues
- Design Principles
	- Test recovery procedures
	- Automatically recover from failure
	- Scale horizontally to increase aggregate system availability
	- Stop guessing capacity
	- Manage change in automation

##### AWS Services
- Foundations: [[IAM]], [[VPC]], Service Limits, Trusted Advisor
- Change Management: [[ASG]], [[CloudWatch]], [[CloudTrail]]
- Failure management: [[Backup]], [[CloudFormation]], [[S3]], [[S3 Glacier Deep Archive]], [[Route 53]]