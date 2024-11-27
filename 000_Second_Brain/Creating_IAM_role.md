12/09/2024 2024

Status #idea

Tags:

# Creating IAM role

Go to the instance created.
Connect to the Linux cli - ls to see whats in the location
aws s3 ls - lists s3 buckets
	if error message then no permissions for the instance. need to set up permissions.
	back to dashboard
		click box for the instance
			then actions
				security
					modify iam
					create new iam role
					select ec2
					then find s3 full access permissions
					give role a name
				create role
			go back to modify role page and refresh
			attach the role created to the iam
		back to linux cli
		aws s3 ls to check, should have no errors now
		[[Create new Bucket]]
		
# References
