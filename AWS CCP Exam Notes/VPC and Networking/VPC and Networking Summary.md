[[VPC]]: Virtual Private Cloud
Subnets: Tied to an [[AZ]], network partition of the VPC
[[Internet Gateway]]: at the VPC level, provide Internet Access
[[NAT Gateway]] / [[NAT Instances]]: give internet access to private subnets
[[NACL]]: Stateless, subnet rules for inbound and outbound
[[Security Group]]s: Stateful, operate at the [[EC2]] instance level or [[ENI]] (Elastic Network Interface)
[[VPC Peering]]: Connect two VPC with non overlapping IP ranges, nontransitive
[[Elastic IP]]: fixed public IPv4, ongoing cost if not in-use
[[VPC Endpoints]]: Provides private access to AWS Services within VPC
[[PrivateLink]]: privately connect to a service in a 3rd party VPC
[[VPC Flow Logs]]: network traffic logs
[[Site to Site VPN]]: VPN over the public internet between on-premises DC and AWS
[[Client VPN]]: OpenVPN connection from your computer into your VPC
[[Direct Connect]]: direct private connection to AWS
[[Transit Gateway]]: Connect thousands of VPCs and on-premises networks together