- A global application is an application deployed in multiple geographies
- On AWS: This could be Regions and / or Edge Locations
- Decreased Latency:
	- Latency is the time it takes for a network packet to reach a server
	- It takes time for a packet from Asia to reach the US
	- Deploy your applications closer to your users to decrease latency, better experience
- Disaster Recovery
	- If an AWS region goes down (earthquake, storms, power shutdown, politics)...
	- You can fail-over to another region and have your application still working
	- A DR plan is important to increase the availability of your application
- Attack Protection: distributed global infrastructure is harder to attack

##### Infrastructure
- Regions: for deploying applications and infrastructure
- Availability Zones ([[AZ]]): Made of multiple data centers
- Edge Locations (Points of Presence): for content delivery as close as possible to users

##### Applications
- Global DNS: [[Route 53]]
	- Great way to route users to the closest deployment with least latency
	- Great for disaster recovery strategies
- Global Content Delivery Network ([[CDN]]): [[CloudFront]]
	- Replicate part of you application to AWS Edge Locations - decrease latency
	- Cache common requests - improved user experience and decreased latency
- [[S3 Transfer Acceleration]]
	- Accelerate global uploads and downloads into [[S3]]
- AWS [[Global Accelerator]]
	- Improve global app availability and performance using the AWS global network