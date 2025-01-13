23/09/2024 0648

Status #idea

Tags:

# Amazon VPC

Amazon VPC is a core service supplied by [AWS](~/Documents/Second_Brain/000_Second_Brain/AWS.md).
It is logically isolated private network for you and your applications within AWS services.
Amazon VPC can be compared to owing a piece of land on the internet, allowing you to create a separate space in the
[AWS](~/Documents/Second_Brain/000_Second_Brain/AWS.md) network you can launch resources in a virtual network that you define.
The VPC that you design are isolated from other VPC's giving you control over your own segment of the cloud. VPC's give you 
complete control over the resources within it. Like [AWS](~/Documents/Second_Brain/000_Second_Brain/AWS.md)
[EC2](~/Documents/Second_Brain/000_Second_Brain/EC2.md) and [RDS](~/Documents/Second_Brain/000_Second_Brain/RDS.md).
These services are placed inside the VPC along with [Networking](~/Documents/Second_Brain/000_Second_Brain/network.md) 
to help control data traffic between your services. There are many components inside the VPC's to understand, such a[[s

		[CIDR Blocks](~/Documents/Second_Brain/000_Second_Brain/CIDR_Blocks.md)
        [Subnets](~/Documents/Second_Brain/000_Second_Brain/Subnets.md)
        [Root Tables](~/Documents/Second_Brain/000_Second_Brain/Root_Tables.md)
        [Internet Gateway](~/Documents/Second_Brain/000_Second_Brain/Internet_Gateway.md)
        [NAT Gateway](~/Documents/Second_Brain/000_Second_Brain/NAT_Gateway.md)
        [Security Groups](~/Documents/Second_Brain/000_Second_Brain/Security_Groups.md)
        [NACL](~/Documents/Second_Brain/000_Second_Brain/NACL.md)'s
		
Real world analogies Summary

[VPC](~/Documents/Second_Brain/000_Second_Brain/VPC.md) - your own piece of land in the cloud
[CIDR Blocks](~/Documents/Second_Brain/000_Second_Brain/CIDR_Blocks.md) - the property lines defining the size of your land
[Subnets](~/Documents/Second_Brain/000_Second_Brain/Subnets.md) - Individual plots of land designated for specific uses
[Root Tables](~/Documents/Second_Brain/000_Second_Brain/Root_Tables.md) - Street signs and traffic rules directing traffic
[Internet Gateway](~/Documents/Second_Brain/000_Second_Brain/Internet_Gateway.md) - The main gate to you property for access to and from the outside world
[NAT Gateway](~/Documents/Second_Brain/000_Second_Brain/NAT_Gateway.md) - A mail forwarding service allowing outbound communications without direct inbound access
[Security Groups](~/Documents/Second_Brain/000_Second_Brain/Security_Groups.md) - Bouncers at each house deciding who gets in or out based on rules
[NACL](~/Documents/Second_Brain/000_Second_Brain/NACL) s - Security checkpoints at the entrance to each plot, checking all traffic against rules.
Learning these will make it easier to manage and configure your private virtual cloud [VPC](~/Documents/Second_Brain/000_Second_Brain/VPC.md)
in [AWS](~/Documents/Second_Brain/000_Second_Brain/AWS.md).




# References
