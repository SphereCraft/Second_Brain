23/09/2024 0648

Status #idea

Tags:

# Amazon VPC

Amazon VPC is a core service supplied by [AWS](./AWS.md).
It is logically isolated private network for you and your applications within AWS services.
Amazon VPC can be compared to owing a piece of land on the internet, allowing you to create a separate space in the [AWS](./AWS.md) network where
you can launch resources in a virtual network that you define. The VPC that you design are isolated from other VPC's giving you control over your
own segment of the cloud. VPC's give you complete control over the resources within it. Like [AWS](./AWS.md) [EC2](./EC2.md) and [RDS](./RDS.md).
These services are placed inside the VPC along with [Networking](./network.md) to help control data traffic between your services. There are many components 
inside the VPC's to understand, such a[[s

		[CIDR Blocks](./CIDR_Blocks.md)
		[Subnets](./Subnets.md)
		[Root Tables](./Root_Tables.md)
		[Internet Gateway](./Internet_Gateway.md)
		[NAT Gateway](./NAT_Gateway.md)
		[Security Groups](./Security_Groups.md)
		[NACL](./NACL.md)'s
		
Real world analogies Summary

[VPC](./VPC.md) - your own piece of land in the cloud
[CIDR Blocks](./CIDR_Blocks.md) - the property lines defining the size of your land
[Subnets](./Subnets.md) - Individual plots of land designated for specific uses
[Root Tables](./Root_Tables.md) - Street signs and traffic rules directing traffic
[Internet Gateway](./Internet_Gateway.md) - The main gate to you property for access to and from the outside world
[NAT Gateway](./NAT_Gateway.md) - A mail forwarding service allowing outbound communications without direct inbound access
[Security Groups](./Security_Groups.md) - Bouncers at each house deciding who gets in or out based on rules
[NACL](./NACL.md)'s - Security checkpoints at the entrance to each plot, checking all traffic against rules.
Learning these will make it easier to manage and configure your private virtual cloud [VPC](./VPC.md) in [AWS](./AWS.md).




# References
