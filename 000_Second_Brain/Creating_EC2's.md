13/10/2024 0944

Status #idea

Tags:

# Creating EC2's

In this training example, we will be creating 2 new [[EC2]]'s one in each private subnet, in each [[AZ]].
Go to [[EC2]] dashboard
launch instance
	will be naming them EC2App2a/2b
in theory we should create a new key pair, but for this example we will be keeping it simple and add the bastion one we created earlier
select correct [[VPC]]
select correct subnet that you want the created [[EC2]] to be in
this does not need a public [[IP Address]]
Security group name EC2App2aSG
	keep name relevant to help with organisation
Add description
	ie EC2 Security Group for AZ 2a/2b
	will change inbound rules later
Launch instance
	If get an error for name, change name
Will create 2 of these, one for each [[AZ]]

Second [[EC2]] doesn't need a key pair
	select relevant option
do the rest same as above


# References
