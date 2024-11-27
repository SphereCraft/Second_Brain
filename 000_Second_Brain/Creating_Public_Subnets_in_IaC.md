14/10/2024 1606

Status #idea

Tags:

# Creating Public Subnets in IaC

Before starting, must ensure the VPC Template is open in VScode as we will be adding the subnet directly to the template.

New Line

PublicSubnet1A:
	Type: 'AWS::EC2::Subnet'
	Properties:
		VpcId: !Ref MyVPC
		CidrBlock: '172.16.1.0/24'
		AvailabilityZone: !Select [0, !GetAZs '']
		MapPublicIpOnLaunch: true
		Tags:
			- Key: Name
				Value: PublicSubnet1A
The AZ property defines which subnet or resource will be created
The GetAZs retrieves a list of the AZ's in the region that the stack was deployed in.
The empty string will use that's stacks region
The !select 0, this picks the first from the list. in programming everything starts from 0, so both together tells the formation to select the first AZ in the region
MapPublicIpOnLaunch means for any subnet that is automatically assigned an IP address. this is important for subnets that need direct access to the internet. For private subnets we wouldn't  set this at all, or set as false.

AppPrivateSubnet1A:
	Type: 'AWS::EC2::Subnet'
	Properties:
		VpcId: !Ref MyVPC
		CidrBlock: '172.16.1.0/24'
		AvailabilityZone: !Select [0, !GetAZs '']
		Tags:
			- Key: Name
				Value: PublicSubnet1A
Deploying is same command
aws cloudformation create-stack --stack-name vpc-stack --template-body file://vpc.yaml
delete if all ready exists
create again
if get rollback error, go to console and look for the error and it should say why, fix, delete and create again.
Also Update-stack is a command


# References
