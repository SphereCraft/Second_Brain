13/10/2024 0953

Status #idea

Tags:

# Updating Security Groups

We are going to allow ssh connection from bastion to EC2App2a
click on EC2App2a
	security tab
Click on SG within 
Click on the security group
	inbound rules
	edit inbound rules
Remove the 'all traffic' 0.0.0.0/0 - delete
add rule
	type - ssh
	source - bastion SG
for second (EC2App2b), just add rule
	type - icmp - IPv4
	source - EC2App2aSG (as we are going to ping to it we need a connection)
	
# References
