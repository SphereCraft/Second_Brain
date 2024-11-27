07/08/2024 0704

Status #idea

Tags:

# Project S3

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

# References
