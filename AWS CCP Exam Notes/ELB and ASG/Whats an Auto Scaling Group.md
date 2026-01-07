[[ASG]] 
- In real life, the load on your websites and application can change
- In the cloud you can create and get rid of servers very quickly
- The goal of an [[ASG]] is to:
	- Scale out (add [[EC2]] instances) to match an increased load
	- Scale in (remove [[EC2]] instances) to match a decreased load
	- Ensure we have a minimum and a maximum number of machines running
	- Automatically register new instances to a [[ELB]]
	- Replace unhealthy instances
- Cost Savings: only run at an optimal capacity (principle of the cloud)

##### ASG contains:
- A minimum size (number of EC2 instances)
- An actual size / desired capacity
- A maximum size
- Scales between these boundaries as necessary
- Works hand in hand with a load balancer