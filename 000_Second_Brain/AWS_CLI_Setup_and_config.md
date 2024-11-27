15/08/2024 2201

Status #idea

Tags:

# AWS CLI Set up and config

# 🚀 Project - AWS CLI - S3 Bucket

##### [Week 2 - Git & Cloud Architecture](https://cloudengineeracademy.mykajabi.com/products/cloud-academy-tech-with-soleyman/categories/2154646443)

### Exercise 1: AWS CLI Setup and Configuration

****Objective:**** Learn how to configure the AWS CLI.

1. Install the AWS CLI following the official AWS documentation.
    
2. Configure the AWS CLI with an IAM user credentials using `aws configure`. Enter your AWS Access Key ID, Secret Access Key, default region name, and default output format.
    

### Exercise 2: Listing S3 Buckets

****Objective:**** Practice listing Amazon S3 buckets using the CLI.

1. Use the `aws s3 ls` command to list all the S3 buckets under your AWS account.
    
2. Identify how many buckets are currently created and document their names.
    

### Exercise 3: Creating an S3 Bucket

****Objective:**** Learn to create an S3 bucket using the CLI.

1. Create a new S3 bucket using `aws s3 mb s3://<your-bucket-name>`, replacing `<your-bucket-name>` with a unique name.
    
2. Verify the bucket was created successfully by listing all buckets.
    

### Exercise 4: Uploading a File to S3

****Objective:**** Practice uploading a file to an S3 bucket.

1. Create a text file named `test.txt` and add some content to it.
    
2. Upload the file to your previously created S3 bucket using `aws s3 cp test.txt s3://<your-bucket-name>/`.
    
3. Verify the file was uploaded successfully by listing the contents of your bucket.
    

  
  

  
  

# 🚀 Project - AWS CLI - IAM User

##### [Week 2 - Git & Cloud Architecture](https://cloudengineeracademy.mykajabi.com/products/cloud-academy-tech-with-soleyman/categories/2154646443)

### Exercise: Creating an IAM User with the AWS CLI

****Objective:**** Learn to create a new IAM user and attach a policy granting them specific permissions using the AWS CLI.

#### ****Part 1: Create a New IAM User****

1. ****Create the IAM user:**** Use the `aws iam create-user` command to create a new IAM user. Replace `<UserName>` with the desired name for the new user.
    
    `aws iam create-user --user-name <UserName>`
    
2. ****Verify the user creation:**** List all IAM users to ensure your new user was created successfully.
    
    `aws iam list-users`
    

#### ****Part 2: Attach a Policy to the New User****

To grant permissions to the user, you'll attach a policy. For this exercise, you'll attach the `AmazonS3ReadOnlyAccess` policy, allowing the user to list and read objects in S3 buckets.

1. ****Attach the policy:**** Use the `aws iam attach-user-policy` command to attach the `AmazonS3ReadOnlyAccess` policy to your newly created user. Replace `<UserName>` with the name of the user you created.
    
    `aws iam attach-user-policy --user-name <UserName> --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess`
    
2. ****Verify the policy attachment:**** Check the attached policies of the user to ensure the `AmazonS3ReadOnlyAccess` policy is attached.
    
    `aws iam list-attached-user-policies --user-name <UserName>`
    

#### ****Part 3: (Optional) Enable Programmatic Access****

If you want your IAM user to interact with AWS services through the AWS CLI or SDKs, you'll need to create access keys for programmatic access.

1. ****Create access keys:**** Generate new access keys for the IAM user.
    
    `aws iam create-access-key --user-name <UserName>`
    
2. ****Store the access keys:**** Make sure to securely store the `AccessKeyId` and `SecretAccessKey` returned by the command. These credentials are needed for the user to authenticate with AWS programmatically.
# References
