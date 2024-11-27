18/11/2024 0934

Status #idea

Tags:

# string

A string in python are within quotes, anything contained in quotes, but must start with a letter or underscore and are also case sensitive and cannot contain python keywords. There are 3 ways of creating strings, single quotes, double quotes or triple quotes

'# Single quotes string'
aws_region = 'eu-west-2'

'# Double quotes string'
ec2_instance = "t2.micro"

'# Multi quotes string'
iam_policy = """
    {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "aws-portal:ViewAccount",
            "Resource": "*"
        },
        
    ]
}
"""

print (aws_region)
print (ec2_instance)
print (iam_policy)








# References
