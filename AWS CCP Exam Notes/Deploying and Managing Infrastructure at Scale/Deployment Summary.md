- [[CloudFormation]]: (AWS Only)
	- Infrastructure as Code ([[IaaS]]): works with almost all of AWS resources
	- Make templates to deploy infrastructure
	- Repeat across Regions and Accounts
- [[Beanstalk]] (ASWS Only):
	- Platform as a service ([[PaaS]]), limited to certain programming languages or [[Docker]]
	- Deploy code consistently with a known architecture: [[ALB]] + [[EC2]] + [[RDS]]
- [[CodeDeploy]] (hybrid): deploy and upgrade any application onto servers
- [[SSM]] (Systems Manager) (hybrid): patch, configure, and run commands at scale across a fleet of instances

##### Dev Services
- CodeCommit: AWS replacement for github (deprecated)
- [[CodeBuild]]: build and test code in AWS
- [[CodeDeploy]]: Deploy code onto servers
- CodePipeline: Orchestration of pipeline (from code to build to deploy)
- [[CodeArtifact]]: Store software packages /dependencies on AWS
- [[CDK]]: Define your cloud infrastructure using a programming language