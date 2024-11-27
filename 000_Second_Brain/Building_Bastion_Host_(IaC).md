17/10/2024 2125

Status #idea

Tags:

# Building Bastion Host (IaC)

Keeping it simple for now and continue on the vpc.yaml file

BastionHost:
	Type: 'AWS::EC2::Instance'
	Properties:
		InstanceType: t2.micro
		KeyName: (Give it a name)
		ImageId: ami number (found in ec2 when launch)(Amazon Machine Image)
		Subnet: !Ref PublicSubnet1A (this needs to be correct for it to work)
		SecurityGroupIds:
			- !Ref BastionSG
		Tags:
			- Key: Name
				Value: BastionHost

BastionSG:
	Type: 'AWS::EC2::Security|Group'
	Properties:
		GroupDescription: 'Enable SSH access'
		VpcId: !Ref MyVPC
		SecurityGroupIngress:
			-IpProtocol: tcp
			FromPort: 22
			ToPort: 22
			CidrIp: (your IP address)(this needs to be correct and add /32 at the end as all IP addresses should have their corresponding prefixes at the end. /32 just means that its referring to only 1 specific IP address.)

Now time to validate everything and see if we can ssh into the BastionHost.
Go to terminal, get in the directory where the downloaded bastion.pem is then run
ssh -i bastion.pem {or name of downloaded file} ec2-user@{the IP address of bastionhost}
Should either get an error message or will see the Amazon logo

To copy the key over, run this command from directory where file is
scp -i bastion.pem{or name of file} bastion.pem {or what you want to call it} ec2-user@{bastionhost IP address}:~/
it should now show that is it's been copied over
Log back into the bastionhost again
ssh -i bastion.pem ec2-user{IP Address}
Run ls to see if anything is in the bastionhost root
This file will be used to Auth into our [[EC2]] [[Server]] in the AppSubnet that we will create when we ping from one to the other, as before.



# References
