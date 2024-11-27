13/10/2024 0959

Status #idea

Tags:

# Coping Key pairs

In this training example

First copy/make note of all 3 [[IP Address]]
	Bastion host
	EC2App2a
	EC2App2b
by selecting them and looking at details in the dashboard#

Open terminal
get into the correct directory (where bastion key pair download is)
enter the same ssh command
	ssh -i {file name} ec2-user@{bastionhost IP address} to connect to the bastion host
Now copy over the key file to this bastion from local machine
	create a new tab/terminal, run this command to copy bastion key file
	scp -i {key file name}{give it a new file name ie "private.pem"} ec2-user@{bastion IP}:~/
Now back to first terminal, the one where connected to bastionhost
ls and now should see the new file that has been copied over

ssh into second [[EC2]]
	ssh -i {"private.pem"} ec2-user@{subnet2a private IP}
	should now be logged in to private subnet 2a
no w to ping into the second [[EC2]] (subnet2b) run command
	ping {IP address of 2b}
ctrl c to end pinging.
Its possible to remove the connection to the EC2 in the [[AWS]] dashboard, by removing the IPv4 rule in the security group, then cannot receive the ping.

[[Terminate EC2]]

# References
