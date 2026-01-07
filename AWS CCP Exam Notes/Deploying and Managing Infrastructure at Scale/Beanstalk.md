- Web App 3-tier

##### Developer problems on AWS
- Dont want to Manage infrastructure
- Just want to deploy code
- Dont want to configure all databases, load balancers, etc\
- Want to scale well

- Most web apps have the same architecture ([[ALB]] + [[ASG]])
- All the developers want is for their code to run!
- possibly across different applications and environments

##### AWS Elastic Beanstalk
- A developer centric view of deploying an application on AWS
- It uses all the component's we've seen before:
	- [[EC2]], [[ASG]], [[ELB]], [[RDS]], etc..
- But its all in one view thats easy to make sense of
- We still have full control over the configuration
- ==Beanstalk = Platform as a Service [[PaaS]]==
- Beanstalk usage is free but you pay for the underlying services

- Managed service
	- Instance configuration / OS is handled by Beanstalk
	- Deployment strategy is configurable but performed by Elastic Beanstalk
	- Capacity provisioning
	- Load balancing and auto-scaling
	- Application health-monitoring and responsiveness
- Just the application code is the responsibility of the developer

##### Three architecture models
- Single instance deployment: good for dev
- LB + [[ASG]]: great for production or pre-production web applications
- [[ASG]] only: great for non-web apps in production (workers, etc...)

- Support for many platforms
	- Go
	- Java SE
	- Java with Tomcat
	- .NET on Windows Server with IIS
	- Node.js
	- PHP
	- Python
	- Ruby
	- Packer Builder
	- Single Container Docker
	- Multi-Container Docker
	- Preconfigured Docker

##### Beanstalk Health Monitoring
- Health agent pushes metrics to [[CloudWatch]]
- Checks for app health, publishes health events

##### Beanstalk is built around deploying code without worrying about the infrastructure while [[CloudFormation]] is built around building the infrastructure from templates