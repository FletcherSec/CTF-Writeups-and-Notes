[[EC2]]:
- Virtual Servers in the Cloud
- Limited by RAM and CPU
- Continuously running
- Scaling means intervention to add / remove servers
---
[[Lambda]]:
- Virtual functions - no servers to manage!=
- Limited by time - short executions
- Run on demand
- Scaling is automated

##### Benefits of Lambda
- Easy Pricing
	- Pay per request and compute time
	- Free tier of 1,000,000 AWS lambda requests and 400K GBs of compute time
- Integrated with the whole AWS suite of services
- Event-Driven: functions get invoked by AWS when needed
- Integrated with many programming languages
- Easy monitoring through AWS [[CloudWatch]]
- Easy to get more resources per functions (up to 10GB of RAM)
- Increasing RAM will also improve CPU and network

##### Lambda language support
- Node.js (javascript)
- Python
- Java
- C# / Powershell
- Ruby
- Custom Runtime API (Rust or Golang)
- Lambda Container Image

Example: Serverless Thumbnail Creation Chain
- When a new image is added in [[S3]], an event triggers a lambda action to push a new thumbnail to [[S3]] and store metadata in a [[DynamoDB]]
- Scales really well and dont need to worry about provisioning

Serverless CRON job
- [[CloudWatch]] Events EventBridge Triggers every 1 hour causing Lambda to perform a task

Payment
- Pay per calls and duration
	- First 1,000,000 requests free
	- $0.20 per 1,000,000 requests thereafter
	- $1.00 for every 600K GB-seconds (RAM)