02/11/2024 0747

Status #idea

Tags:

# Terraform

Terraform configuration files are similar to cloudformation Templates
Terraform files will have a .tf file extension.
These files have 4 common things
	*Providers* - Define which cloud provider or service Terraform will interact with.provider block contains which provider and region, this is very important as without it nothing else will work. Also tags that are useful for organising but are optional.
	*Resources* - Describes the infrastructure components you want to create. The resource block defines the resource, ie [[EC2]] with its corresponding ami number.
	*Variables* - Help make your configuration more flexible and reusable. he variable block defines, ie an instance type, which is referenced in other blocks for greater flexibility.
	*Outputs* - Specifies the output values you want to retrieve after applying your configuration. Output Block will display, ie the [[EC2]] instance, object value.

***Terraform Resources***
Inside the {} the ami number, instance_type and tags, these are like the properties in cloudformation. The first line, ie
resource "aws_instance" "myec2" 
the aws_instance is the service you want, in this case an [[EC2]] and the myec2 is the name of it for referencing in other blocks







# References
