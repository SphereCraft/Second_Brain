19/09/2024 0716

Status #idea

Tags:

# Subnets

Subnets in Amazon AWS [[VPC]] are designated areas that serve unique roles or functions, they are sub divisions of your [[VPC]]'s IP address range that allow you to segment and organise your cloud resources based on varying levels of access and security needs, this helps with traffic management, security and network policies.
Public subnet can have resources that can be directly accessed from the internet, this is enabled through an internet gateway [[IGW]], a [[VPC]] component between the public subnet and the internet. Every service in a public subnet must have a public IP address or an Elastic IPv4 address to be accessed. The subnet route table must contain a route to the [[IGW]]. Public subnets are good for 
		[[Front End]] web servers
		Public [[API]]'s
		Services that require direct interaction with users or external systems over the internet
		
Private subnets are designed for resources that should not be directly accessed from the internet. Resources from these subnets can communicate with each other and with public subnets. Private subnets do not have routes to the [[IGW]] in there table, instead they must access through the [[NAT Gateway]] which allows outbound traffic but not unsolicited inbound traffic. Private subnets are typically used for
			[[Back End]] servers
			[[Database]]
			High security application logic layers
Learning this is important for functionally and security of the [[VPC]].
Organising the subnets you can enhance security by separating sensitive and critical workloads from public facing services reducing the risk of unauthorised access. Improve performance by localising traffic, minimise latency and maximise throughput, especially when using closely related services like, application services - databases.
Can add clear roles and policies to each subnet to help simplify the management making it easier to 
	manage access controls
	monitor traffic
	data governance requirements

Subnets are a way of dividing the [[VPC]] into smaller sections. Each section can server a certain purpose, these could include
	Public facing - can access via the internet
	Private - only accessed by you
A [[VPC]] can have many different subnets, like the 3 tier application
	public - [[Front End]]
	private - [[Business Logic]]
	Private - [[Database]] services
Subnets help keep boundaries between public and private. Organise subnets based on internet access, only use public subnets when its controlled and needed.
# References
