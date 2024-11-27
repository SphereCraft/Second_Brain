21/10/2024 1404

Status #idea

Tags:

# Creating IAM user in IaC

As usual start with 

AWSTemplateVersion: '2010-09-09'
Description: 'IAM Cloudformation template'

Resources:
MyIAMUser:
	Type: 'AWS::IAM::User'
	Properties:
		UserName: 'JeffCFN'
		ManagedPolicyArns:
			- 'arn:aws:iam:aws:policy/AdministratorAccess'

Same create-stack command to deploy
aws cloudformation create-stack --stack-name iam-stack --template-body file://iam.yaml
but when adding a new [[IAM]] with admin access, this is a very powerful access to give, so [[AWS]] will ask if you are sure and if so it want you top add to the command, in this case its --capabilities CAPABILITY_NAMED_IAM, add this to the end of the command and it should deploy correctly.
||Access keys and passwords do not go into the code for obvious reasons, this needs to be done via the console.
Creating Group
# My IAM Group

MyIAMGroup:

Type: 'AWS::IAM::Group'

Properties:

GroupName: 'JeffGroup'

  

# Attach User to Group

UserToGroup:

Type: 'AWS::IAM::UserToGroupAddition'

Properties:

GroupName: !Ref MyIAMGroup

Users:

- !Ref MyIAMUser

  

# IAM Role for EC2

MyIAMRole:

Type: 'AWS::IAM::Role'

Properties:

AssumeRolePolicyDocument:

Version: '2012-10-17'

Statement:

- Effect: 'Allow'

Principal:

Service: ['ec2.amazonaws.com']

Action: ['sts:AssumeRole']

ManagedPolicyArns:

- 'arn:aws:iam::aws:policy/PowerUserAccess'

  

# S3 Custom Policy

MyIAMPolicy:

Type: 'AWS::IAM::Policy'

Properties:

PolicyName: 'CustomPolicy'

PolicyDocument:

Version: '2012-10-17'

Statement:

- Effect: 'Allow'

Action:

- "s3:GetObject"

Resource: '*'

Roles:

- !Ref MyIAMRole

Version of the policy language - this is most up to date.
Statement declares what actions are allowed or declined
Effect is either allow or deny - Allow permits whats in the statement
Principal defines who is allowed to preform the actions in this case its an [[AWS]] service [[EC2]].
ManagedPolicyArns is the attached policy, this example is PowerUserAccess, this will not give full access.

Deploy, fix errors.
Always check formatting and syntax.
# References
