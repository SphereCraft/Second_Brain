21/10/2024 0725

Status #idea

Tags:

# Building EC2 in IaC

As before, keep code simple and 'pretty', use good indentations.

*# App Instance 1A*
AppInstance1A:
	Type: 'AWS::EC2::Instance'
	Properties:
		InstanceType: t2.micro
		KeyName: bastion (in this example)
		ImageId: ami 0000 (see [[AMI Key]] to find)
		SubnetId: !Ref AppPrivateSubnet1A
		SecurityGroupIds:
			- !Ref AppInstance1ASG
		Tags:
			- Key: Name
				Value: App1
Can copy and paste but change name to 2B to create second instance in AZ2. no keyname needed for this one as not needed in subnet 2 for this exercise. 2nd App instance will need a new security group, so give it a different name too.

First security group will reference the connection to the bastion server, second one will reference the connection to the first app instance. (same as when we did it in the console).

*#SG App 1A*
AppInstance1ASG: (this needs to be the same as the reference in the subnet)
	Type: 'AWS::EC2::Security Group'
	Properties:
		GroupDescription: 'Allow SSH from Bastion'
		VpcId: !Ref MyVPC
		SecurityGroupIngress:
			- InProtocol: tcp
				FromPort: 22
				ToPort: 22
				SourceSecurityGroupId: !Ref BastionSG (ref the bastion SG)

Copy and past for the second SG but change the relevant details to suit, ie rename to 2B
GroupDescription: 'Allow ICMP ping from App1'
	- IpProtocol: icmp
		FromPort: -1
		ToPort: -1
		SourceSecurityGroupId: !Ref AppInstance1ASG

Have to pass SG instead of IP because its more flexibly to use the SG rather than individual IP addresses.

Update stack, fix any bugs




# References
