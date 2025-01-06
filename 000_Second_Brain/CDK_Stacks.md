22/11/2024 0619

Status #idea

Tags:

# CDK Stacks

import * as cdk from 'aws-cdk-lib';
import { Construct } from 'constructs';
// import * as sqs from 'aws-cdk-lib/aws-sqs';

interface MyBucketProps {
    bucketName: string;
    versioned: boolean;
    encryption: s3.BucketEncryption;
}
export class CdkProjectStack extends cdk.Stack {
  constructor(scope: Construct, id: string, props?: cdk.StackProps) {
    super(scope, id, props);

    // The code that defines your stack goes here

    const bucketProps: MyBucketProps = {
        bucketName: 'My-S3-Bucket-JJ-CDK-' + this.account,
        versioned: true,
        encryption: s3.BucketEncryption.S3_MANAGED,
    }

        new s3.Bucket(this, 'MyFirstBucket', bucketProps)
  }
}
This is declaring a new S3 Bucket with [Typescript](/home/jeff/Documents/Second_Brain/000_Second_Brain/Typescript.md) and [CDK](/home/jeff/Documents/Second_Brain/000_Second_Brain/cdk.md)

Import - imports the modules to add [CDK](./CDK.md) and [S3](./S3.md)
Export - defines a new class 'myStack' that represents a [CloudFormation Template](./CloudFormation_Template.md)
Constructor - 3 parameters
				scope - parent construct - typically the app
				ID - unique ID from within the stack
				Props - optional properties
Super - this calls the constructor of the parent class

Last part defines the [S3](./S3.md) bucket. This is the current stack. 'MyBucket' is the logical ID for the bucket within this stack.
The object 
	versioning = true - this allows versioning
	encryption - adds s3 encryption.

Key components of [CDK](./CDK.md) stack

We declare the infrastructure with [CDK](./CDK.md) and [Typescript](./Typescript.md) and [CDK](./CDK.md) will create the template, 
then deploys that to [AWS](./AWS.md). when you look in the console its like you deployed using [Cloudformation](./CloudFormation_Template.md).
This allows us to use [Typescript](./Typescript.md) that help simplify it all.
A project would typically look like (folders)

my-cdk (project)
		/lib
file - my-stack.ts

After [Installing CDK](./Installing_CDK.md) we can create a [New CDK Project](./New_CDK_Project.md)







# References
