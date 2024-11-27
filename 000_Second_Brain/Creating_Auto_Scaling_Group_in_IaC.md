26/10/2024 1041

Status #idea

Tags:

# Creating Auto Scaling Group in IaC

First we will setup a launch configuration, this will include what [[EC2]]'s we want to make. Will also build the [[EC2]]'s, build the [[ASG]] (auto scaling group).
We want minimum of 1 [[EC2]] and a maximum of 3 [[EC2]]'s with a desired amount of 2. Also set cloudwatch so when the CPU reaches 70% it will automatically create a new [[EC2]] instance - scaling up.
We cant replicate this exactly as we are not currently working with live traffic.

So to start, in VSCode, create new file and call it asg.yaml
Copy and past everything from the ec2.yaml file above '#ApplicationLoadBalancer' to save time.
Copy and past the WebServerSecurityGroup, then add:

'#Launch Config'
MyLaunchConfiguration:
	Type: 'AWS::AutoScaling::LaunchConfiguration'
	Properties:
		ImageId: 'ami-00000'   (Same as before)
		InstanceType: 't2.micro'
		SecurityGroup:
			- !Ref WebServerSecurityGroup
		UserData:
			Fn::Base64: !Sub |
			#!/bin/bash
			yum install -y httpd
			systemctl start httpd
			systemctl enable httpd
			echo "Hello from Auto Scaling Instance" > /var/www/html/index.html

'#ASG'
MyAutoScalingGroup:
	Type: 'AWS::AutoScaling::AutoScalingGroup'
	Properties:
		LaunchConfigurationName: !Ref MyLaunchConfiguration
		MinSize: 1
		MaxSize: 3
		DesiredCapacity: 2
		VPCZoneIdentifier:
			- !Ref PublicSubnet1A
			- !Ref PublicSubnet2B

Setting up the High CPU Alarm

'# Alarm'
HighCPUAlarm:
	Type: 'AWS::CloudWatch::Alarm'
	Properties:
		AlarmDescription: 'Alarm when CPU exceeds 70%'
		MetricName: 'CPUUtilization'
		NameSpace: 'AWS/EC2'
		Statistic: Average
		Period: '300'
		EvaluationPeriods: '1'
		Threshold: '70'
		ComparisonOperator: GreaterThanThreshold
		Dimension:
			- Name: AutoScalingGroupName
				Value: !Ref MyAutoScalingGroup
		AlarmActions:
			- !Ref ScaleOutPolicy
Statistic is the, in this case, average of the period (300) and if it exceeds the evaluation period by 1, in this case, then it will trigger the comparison operator, which is then referenced to the auto scaling group.

And finally adding the ScaleOutPolicy

'#Scale Out Policy'
ScaleOutPolicy:
	Type: 'AWS::AutoScaling::ScalingPolicy'
	Properties:
		AutoScalingGroupName: !Ref MyAutoScalingGroup
		PolicyType: SimpleScaling
		ScalingAdjustment: '1'
		Cooldown: 300
		AdjustmentType: ChangeInCapacity

This defines the scaling policy
Scaling adjustment tells it how many to scale up or down at any one time.
Then the cooldown period of 300, in this case' before doing another adjustment. This should give it enough time to complete any action before looking again. this should keep it all stable.

Can now deploy in the usual way with the same command to create-stack.
Check in the console to see if its been deployed correctly and then can look at all the sections to see how the auto scaling has been configure. Cannot look at how it works as no live traffic yet.


# References
