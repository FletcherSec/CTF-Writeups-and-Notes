- Stands for "Virtual Private Cloud"
- VPC is something you should know in depth for the AWS Certified Solutions Architect Associate and AWS Certified SysOps Administrator
- For CCP know:
	- [[VPC]], Subnets, Internet Gateways, and NAT Gateways
	- Security Groups, Network ACL (NACL), VPC Flow Logs
	- VPC Peering, VPC Endpoints
	- Site to Site VPN and Direct Connect
	- Transit Gateway

##### VPC
- Private network to deploy your resources (regional resource)
- Subnets allow you to partition your network inside your VPC (Availability Zone resource)
- A public subnet is a subnet that is accessible from the internet
- A private subnet is a subnet that is not accessible from the internet
- To define access to the internet and between subnets, we use [[Route Tables]]