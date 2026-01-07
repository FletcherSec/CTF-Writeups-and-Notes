- On-Demand Instances - short workload, predictable pricing, pay by second
- Reserved (1 and 3 years)
	- Reserved instances - long workloads
	- Convertible Reserved Instances - long workloads with flexible instances
- Savings Plans (1 and 3 years) - commitment to an amount of usage, long workload
- Spot Instances - short workloads, cheap, can lose instances (less reliable)
- Dedicated Hosts - book an entire physical server, control instance placement
- Dedicated Instances - no other customers will share your hardware
- Capacity Reservations - reserve capacity in a specific AZ for any duration

##### EC2 on Demand
- Pay for what you use:
	- Linux or Windows - billing per second after the first minute
	- All other OS - billing per hour
- Has the highest cost but no upfront payment
- No long-term commitment

- Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave

##### EC2 Reserved Instances
- Up to 72% discount compared to On-demand
- You reserve a specific instance attributes (Instance Type, Region, Tenancy, OS)
- Reservation Period - 1 year (+discount) or 3 years (+++discount)
- Payment Options - No upfront (+), Partial Upfront (++), All Upfront (+++)
- Reserved Instance's Scope - Regional or Zonal (reserve capacity in an AZ)
- Recommended for steady-state usage applications (think database)

- Special type of Reserved Instance: Convertible Reserved Instance
	- Can change the EC2 instance type, instance family, OS, scope, and tenancy
	- Up to 66% discount

##### EC2 Savings Plans
- Get a discount based on long-term usage
- Commit to a certain type of usage ($10/hour for 1 or 3 years)
- Usage beyond EC2 Savings Plans is billed at the On-Demand price

- Locked to a specific instance family and AWS region (like M5 in us-east-1)
- Flexible across:
	- Instance size (m5.xlarge, m5.2xlarge)
	- OS (Linux, Windows)
##### EC2 Spot Instances
- Can get a discount of up to 90% compared to On-demand
- Instances that you can "lose" at any point of time if your max price is less than the current spot price
- The MOST cost-efficient instances in AWS
- Useful for workloads that are resilient to failure

##### EC2 Dedicated Hosts
- A physical server with EC2 instance capacity fully dedicated to your use
- Allows you to address compliance requirements and use your existing server-bound software licenses (per-socket, per-core, pe - VM software licenses)
- Purchasing Options:
	- On-demand - pay per second for active Dedicated Host
	- Reserved - 1 or 3 years (No Upfront, Partial Upfront, All Upfront)
- The most expensive option

- Use case for software with complicated licensing models (BYOL - Bring your own license)
- Or for companies that have a strong regulatory or compliance need

##### EC2 Dedicated Instances
- Instances that run on hardware thats dedicated to you
- May share hardware with other instances in same account
- No control over instance placement (can move hardware after Stop / Start)

##### EC2 Capacity Reservations
- Reserve On-Demand instances capacity in a specific AZ for any duration
- You always have access to EC2 capacity when you need it
- No time commitment (create/cancel anytime), no billing discounts
- Charged On-Demand rate whether you run instances or not

![[Pasted image 20251209131620.png]]