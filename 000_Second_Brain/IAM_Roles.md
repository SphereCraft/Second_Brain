21/10/2024 2149

Status #idea

Tags:

# IAM Roles

These are identities that show what they can and cannot do within [[AWS]], unlike users, roles do not have access keys or passwords. Instead when you assign a role it will provide a short term security credentials for you role session. Roles are to delegate permissions to a user or service to gain access to those that you trust to do a task.
Cross account access roles - being able to get access to other services to help or to 
allow a service to access another service, like when we allowed an EC2 instance access to data in an S3 bucket, allowing it to read the objects. This is more secure way of allowing access to other services.
Just remember to only allow fine control access, not full access.




# References
