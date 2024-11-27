16/10/2024 1932

Status #idea

Tags:

# Rooting in IaC

InternetGateway:
	Type: 'AWS::EC2::InternetGateway'
	Properties:
	Tags:
		- Keys: Name
			Value: MyVPC-IGW
This will define an IGW (not real, its an EC2 replacement for this exercise)

AttachGateway:
	Type: 'AWS::EC2::VPCGatewayAttachment'
	Properties:
		VpcId: !Ref MyVPC
		InternetGatewayId: !Ref InternetGateway
Attaches the IGW to the VPC

PublicRouteTable:
	Type: 'AWS::EC2::RouteTable'
	Properties:
		VpcId: !Ref MyVPC
		Tags: 
			- Key: Name
				Value: PublicRouteTable
Determines where the network traffic from the subnet is directed

PublicRoute:
	Type: 'AWS::EC2::Route'
	DependsOn: AttachGateway
	Properties:
		RouteTableId: !Ref PublicRouteTable
		DestinationCidrBlock: '0.0.0.0/0'
		GatewayId: !Ref InternetGateway
Defines a route inj the table. RouteTable belongs to the above table, Cidr Block is all traffic and GatewayId indicates the path to internet

PublicSubnet1ARouteTableAssociation:
	Type: 'AWS::EC2::SubnetRouteTAbleAssociation'
	Propperties:
		SubnetId: !Ref PublicSubnet1A
		RouteTableId: !Ref PublicRouteTable
This determines the association of the public root table to the subnet.

To Deploy, can use the update command instead of create, rest of command is the same, just replace the first create with update.
If any error, find, debug and try again
aws cloudformation update-stack --stack-name vpc-stack --template-body file://vpc.yaml



# References
