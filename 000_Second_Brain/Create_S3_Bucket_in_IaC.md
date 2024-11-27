30/10/2024 2036

Status #idea

Tags:

# Create S3 Bucket in IaC

In this example we will create an S3 bucket with a basic static website and create bucket policies, all in IaC.
Go to VSCode and create a new file and call it s3-static.yaml
Then usual start

AWSTemplateFormatVersion: '2010-09-09'
Description: 'S3 Static file Hosting'

Resources:
	'# My S3 Bucket'
	MyS3Bucket:
		Type: 'AWS::S3::Bucket'
		Properties:
			BucketName: '(give the bucket a global unique name)'
			WebsiteConfiguration:
				IndexDocument: 'index.html' (need to create this file)
Now need to create the index.html file.
Create new file called index.html

		<!DOCTYPE html>
		
		<html>
		<head>
		
			<title>My S3 Hosted Website</title>
		
		</head>
		<body>
			<h1>Welcome to S3 hosted Website</ht>
		</body>
		
		</html>
Now create the stack in the usual way and correct any errors.
Copy the index.html file to the bucket using this command
aws s3 cp index.html s3://(the unique name given to the bucket)
file should now be uploaded to the bucket.
We now go to the console to validate, should see the index.html, but when trying to view the file you should see 'access denied', this is due to the fact that the link is a public access and all public access is denied, so will need to update the policy/write a new policy, so back into VSCode to create this.

Adding to the s3-static.yaml in aliment with WebSiteConfiguration

PublicAccessBlockConfiguration:
	RestrictPublicBuckets: False (this by default is true)

'# Bucket Policy'
BucketPolicy:
	Type: 'AWS::S3::BucketPolicy'
	Properties:
		Bucket: !Ref MyS3Bucket (reference the policy above)
		PolicyDocument:
			Version: '2012-10-17'
			Statement:
				- Sid: 'PublicReadGetObject' (specific policy name id to help find)
					Effect: 'Allow' (what will happen)
					Principal: 'star' (Defines entity it applies to, the star is all)
					Action: 'S3:GetObject' (action statement allow) 
					Resource: !Sub 'arn:aws:s3:::${MyS3Bucket}/star'

Update the stack in the usual way
Now, should be able to see the bucket policy in the console that we created, it should be in the resources tab. And then should be able to access the index.html that we created as we set the policy top be open to all.

Thinking bigger and in the future, this example is simple and to make any changes to the index.html is quite simple, but if we were in a team of people all working on a larger and more complex project, how would we all know what changes are being made? This is where pipelines and github come into play, so we could all track changes. This is future lessons, but worth thinking about.




# References
