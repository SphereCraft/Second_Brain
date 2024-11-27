02/11/2024 0936

Status #idea

Tags:

# Terraform Architecture

3 main concepts
	[[Terraform]] core aka [[Terraform]] [[CLI]]
	[[Terraform]] providers are modules that enable [[Terraform]] to communicate with a range of services, such as [[AWS]], [[Azure]] and [[GCP]].
	[[Terraform]] State File is a JSON file that stores information of the resources that [[Terraform]] manages as well as their current state. The state file can be kept locally or remotely in an [[S3]] for example, but its very important to keep these files up to date and backed up. As these are the files that [[Terraform]] will use to compare current start with the desired state and decide what needs to be changed when you make changes or modify your infrastructure.





# References
