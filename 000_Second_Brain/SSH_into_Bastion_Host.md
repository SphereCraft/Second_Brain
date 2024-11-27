13/10/2024 0931

Status #idea

Tags:

# SSH into Bastion Host

Click on Bastion Host in the EC2 instances
select public IPv4 address and copy
Go to Terminal
Get to the directory where downloaded file is
	this is to connect to the [[EC2]] BastionHost via ssh
run command
	ssh -i {file name} ec2-user@{paste IP address copied for bastionhost}
	if first time, might get a fingerprint error, just type yes
then could get a permissions error, is so
	command chmod 200 {file name}
	this will change permissions for the file
doing this replicates a [[NAT Gateway]], doing this in training as we know [[NAT Gateway]] cost to have running.
If moved location between steps, either
	change inbound IP address rule and create new one.
	or do whole process again
	or wait until back at same location.
Best practice, do it all at same time in same location

# References
