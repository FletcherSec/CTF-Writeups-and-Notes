- [[CloudWatch]] provides metrics for every service in AWS
- Metric is a variable to monitor (CPUUtil, Networking...)
- Metrics have timestamps
- Can create [[CloudWatch]] dashboards of metrics

##### Important Metrics
- [[EC2]] instances: CPU Utilization, Status Checks, Network (not RAM)
	- Default metrics every 5 minutes
	- Option for Detailed Monitoring ($) metrics every 1 minute
- [[EBS]] volumes: Disk Read/Writes
- [[S3]] buckets: BucketSizeBytes, NumberOfObjects, AllRequests
- Billing: Total Estimated Charge (only in us-east-1)
- Service Limits: how much you've been using a service API
- Custom metrics: push your own metrics

##### CloudWatch Alarms
- Alarms are used to trigger notifications for any metric
- Alarms actions...
	- Auto Scaling: increase or decrease [[EC2]] instances "desired" count
	- [[EC2]] Actions: stop, terminate, reboot, or recover an [[EC2]] instance
	- [[SNS]] notifications: send a notification into an SNS topic
- Various options (sampling, %, max, min, etc....)
- Can choose the period on which to evaluate an alarm
- Example: create a billing alarm on the CloudWatch Billing metric
- Alarm States: OK, INSUFFICIENT_DATA, ALARM