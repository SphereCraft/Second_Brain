13/10/2024 1912

Status #idea

Tags:

# CloudFormation Template

We will be using the last example but will be doing it all in code. need to make sure a few things are set up first.
Should all ready have done 
	[[AWS CLI Set up and config]]
	[[VSCode]]
	Configured [[AWS CLI Set up and config]] with the accesses keys
Next go to github and make a new code repository and call it JeffCloudFormation
clone it to local machine.
Go to desired [[IED]]
get in correct directory
create  new file called s3-bucket.yaml
This needs to be inside of the github repo that was just created.
At the start of all templates there are 2 things 
	CloudFormationTemopoVersion
	description
AWSTemplateFormatVersion: '2010-09-09' - Specifies version '2010-09-09' there others
Description: 'CloudFormation template for S3 bucket' - brief description
Resources: (this defines what resources in stack)
	S3Bucket: (logical name to be referenced)
		Type: 'AWS::S3::Bucket' - most are defined like this
		Properties: - define config of s3-bucket
			BucketName: (Global unique name like 'jeff-s3-bucket.yaml') - across all accounts
To deploy to [[AWS]]
	first save it
	then either,
		use terminal
		or the terminal in VScode
	run
		aws cloudformation create-stack --stack-name my-s3-bucket-stack --template-body file://s3-bucket.yaml (this is the file name created for the template at the start)
	Should now see stack being created
	To check progress
		aws cloudformation describe-stacks --stack-name my-s3-bucket-stack
	If get an error go to the dashboard to view what the issue was then debug
Go to the cloudformation dashboard, should see the created bucket with error, click on it and should see why, fix.
delete stack before trying again, either 
	in the console
	or terminal aws cloudformation delete-stack --stack-name my-s3-bucket-stack
run describe to check
try again with same create stack command
when says create complete it should be done.
check in the dashboard

Creating a [[VPC]] in code
same process except code slightly different
New File called vpc.yaml

AWSTemplateFormatVersion '2010-09-09'
Description: 'CloudFormation for VPC'
Resources:
	MyVPC:
	Type: 'AWS::EC2::VPC' - similar but slightly different for a [[VPC]]
	Properties:
		CidrBlock: '172.16.0.0/16'
		EnableDnsSupport: true
		EnableDnsHostnames: true
		Tags:
			- Key: Name
				Value: MyVPC
Save it
same create stack command but with the vpc.yaml file name



# References
