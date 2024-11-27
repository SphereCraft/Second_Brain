01/11/2024 0658

Status #idea

Tags:

# Terraform vs CloudFormation

[[Cloudformation]] ia an [[AWS]] service specifically for [[AWS]] infrastructure using JSON or YAML files. It also groups resources into stacks.
*Advantages*
	[[AWS]] specific - optimised for [[AWS]]
	Managed service - [[AWS]] controls managing, provisioning and roll backs

*Disadvantages*
	[[AWS]] lock in - only works with [[AWS]]
	Write a lot of code - lots of code for a relative small thing which makes it harder to maintain

[[Terraform]] uses declarative syntax called [[HCL]] that is human readable
uses multi cloud - can use across all cloud providers
state - management across state file
Modular

*Advantages*
	Cloud Agnostic - multi platform cloud providers
	Big community

*Disadvantages*
	Learning curve is steep
	State management is complex
	Licences - no longer free for enterprise level
 [[Cloudformation]] is best for [[AWS]]
 But [[Terraform]] is more versatile




# References
