25/09/2024 0647

Status #idea

Tags:

# Security Groups

These have rules to help protect the services in the [[Subnets]], how things can access and leave (inbound and outbound traffic). 
These rules are default and contain
	[[Protocol]]
	[[IP Address]]
	and a reason for entering ([[Port Number]])
This ensures only approved visitors can gain acesss.
A unique feature, they are [[Stateful]], meaning once someone has been granted access, they are remembered. This will help keep your instances safe.

The [[Security Groups]] will protect the instance within the subnet and the NACL's will protect the [[Subnets]]. This gives and extra layer of protection at the [[Subnets]] level.
# References
