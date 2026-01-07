- [[NACL]] (Network ACL)
	- A firewall which controls traffic from and to subnets
	- Can have ALLOW and DENY rules
	- Are attached at the Subnet level
	- Rules only include IP addresses
- [[Security Group]]s
	- A firewall that controls traffic to and from an [[EC2]] instance
	- Can have only ALLOW rules
	- Rules include IP addresses and other security groups

##### Takeaway: NACL is at subnet level and Security Groups are at EC2 level