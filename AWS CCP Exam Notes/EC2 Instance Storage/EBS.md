- An [[EBS]] is an (Elastic Block Store) Volume is a network drive you can attach to your instances while they run
- It allows your instances to persist data, even after their termination
- They can only be mounted to one instance at a time
- They are bound to a specific availability zone

Analogy: Network USB stick

##### EBS Volume
- Network drive (not physical)
	- Uses the network to communicate with instance meaning there may be some latency
	- Can be detached from one instance to another very quickly
- Locked to an Availability Zone ([[AZ]])
	- An EBS volume in us-east-1a cannot be attached to us-east-1b
	- To move a volume across, you first need to snapshot it
- Have a provisioned capacity (size in GBs and IOPS)
	- You get billed for provisioned capacity
	- You can increase the capacity of the drive over time
- You can have multiple EBS per EC2 instance but only one EC2 instance per EBS (EBS cannot point to more than one EC2 instance)
##### EBS - Delete on Termination Attribute (IMPORTANT)
- Controls the EBS behavior when an EC2 instance terminates
- Delete on termination is default enabled for ROOT and default disabled for other EBS Volumes
- Can be changed in AWS console