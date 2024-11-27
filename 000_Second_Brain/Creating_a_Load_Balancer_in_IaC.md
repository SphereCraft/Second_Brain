26/10/2024 1003

Status #idea

Tags:

# Creating a Load Balancer in IaC

In this next example we will build a load balancer and directing the traffic to 2 targets - [[EC2]] instances, all in IaC

In VScode, create new file and call it ec2.yaml
Copy and paste everything above bastionhost from the vpc file to save some time.

'# Application Load Balancer'
MyLoadbalancer:
	Type: 'AWS::ElasticLoadBalancingV2::LoadBalancer'
	Properties:
		Subnets:
			- !Ref PublicSubnet1A (reference public subnet name)
			- !Ref PublicSubnet2B
		SecurityGroups:
			-Ref: WebServerSecurityGroup (to be created yet)

'# Target Group for ALB'
MyTargetGroup:
	Type: 'AWS::ElasticLoadBalancingV2::TargetGroup'
	Properties:
		VpcId: !Ref MyVPC
		Port: 80
		Protocol: 'HTTP'

'#Listener'
MyListener:
	Type: 'AWS::ElasticLoadBalancerV2::Listener'
	Properties:
		DefaultAction:
			- Type: 'forward'
			TargetGroupArn: !Ref MyTargetGroup
		LoadBalancerArn: !Ref MyLoadBalancer
		Port: '80'
		Protocol: 'HTTP'

All code is generally descriptive, Just connect the dots and should see excatly what is happening.

'#WebServerInstance1A'
WebServerInstance1A:
	Type: 'AWS::EC2::Instance'
	Properties:
		InstanceType: 't2.micro'
		ImageId: 'ami-0000'  (search for the [[EC2]] ami number in console)
		SubnetId: !Ref PublicSubnet1A
		SecurityGroupIds:
			 - !Ref WebServerSecurityGroup
		Tags:
			- Key: 'Name'
				Value: 'WebServerInstance1A'
		UserData:
			Fn::Base64: !Sub |
				#!/bin/bash
				yum install -y httpd
				systemctl start httpd
				systemctl enable httpd
				echo "Hello from My Web Server 1A" > /var/www/html/index.html
					(this is just a demo to prove we made contact with the ec2)

UserData onwards, this script is using user data to install an Apache web server using yum package manager, then starts the service and boots from start, then shows us the message.
This is a way of using pre-configured servers.
Copy and paste for [[EC2]] instance 2B but make sure to change all the relevant details and change the message to 2B.

Then above WebServerInstance1A

'# Web Server / ALB Security Group'
WebServerSecurityGroup:
	Type: 'AWS::EC2::SecurityGroup'
	Properties:
		GroupDescription: 'Enable HTTP Access'
		VpcId: !Ref MyVPC
		SecurityGroupIngress:
			- IpProtocol:: 'tcp'
			FromPort: '80'
			ToPort: '80'
			CidrIp: '0.0.0.0/0'

Then deploy using the same command in the terminal as usual
aws cloudformation create-stack --stack-name ec2-stack --template-body file://ec2.yaml
Traffic comes in and goes to the target group......
Add in the targets in the MyTargetGroup code

Targets:
	- Id: !Ref WebServerInstance1A
	- Id: !Ref WebServerInstance2B
Update using the normal command
aws cloudformation update-stack --stack-name ec2.yaml --template-body file://ec2.yaml
fix any syntax errors
can now go to the console and check if its working
Go to [[EC2]] in the console, find load balancers, copy DNS, go to web page, add HTTP:// and paste the DNS address (might need to allow unsecured access) and should see message appear.

# References
