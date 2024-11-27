23/09/2024 0648

Status #idea

Tags:

# Amazon VPC

Amazon VPC is a core service supplied by [[AWS]].
It is logically isolated private network for you and your applications within AWS services.
Amazon VPC can be compared to owing a piece of land on the internet, allowing you to create a separate space in the [[AWS]] network where you can launch resources in a virtual network that you define. The VPC that you design are isolated from other VPC's giving you control over your own segment of the cloud.
VPC's give you complete control over the resources within it. Like [[AWS]] [[EC2]] and [[RDS]]. These services are placed inside the VPC along with [[Networking]] to help control data traffic between your services.
There are many components inside the VPC's to understand, such a[[s

		[[CIDR Blocks]]
		[[Subnets]]
		[[Root Tables]]
		[[Internet Gateway]]
		[[NAT Gateway]]
		[[Security Groups]]
		[[NACL]]'s
		
Real world analogies Summary

[[VPC]] - your own piece of land in the cloud
[[CIDR Blocks]] - the property lines defining the size of your land
[[Subnets]] - Individual plots of land designated for specific uses
[[Root Tables]] - Street signs and traffic rules directing traffic
[[Internet Gateway]] - The main gate to you property for access to and from the outside world
[[NAT Gateway]] - A mail forwarding service allowing outbound communications without direct inbound access
[[Security Groups]] - Bouncers at each house deciding who gets in or out based on rules
[[NACL]]'s - Security checkpoints at the entrance to each plot, checking all traffic against rules.
Learning these will make it easier to manage and configure your private virtual cloud [[VPC]] in [[AWS]].
# References
