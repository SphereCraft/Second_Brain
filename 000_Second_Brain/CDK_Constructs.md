23/11/2024 0921

Status #idea

Tags:

# CDK Constructs

Constructs are the fundamental  building block of [[CDK]] applications. They represent everything to create [[AWS]] applications.
There are three types of constructs
	L1 Constructs
	L2 Constructs
	L3 Constructs

L1 Constructs are the low level constructs that directly (1:1) represent all [[AWS]] resources in the [[Cloudformation]]. They offer full control, but require configuration. In this example we are using a cfn Bucket that corresponds every detail of what we want the bucket . this is like writing in [[Cloudformation]].

L2 Constructs, these are higher level intent based constructs that provide sensible defaults for working with L1 constructs

L3 Constructs, these are the highest level constructs that represent multi resource patterns or even complete applications. We can use L3 constructs to implement common application patterns to help speed up things.

In general we want to be using L2 constructs for most of our work but back to L1 when we need to fine grain control.


import * as cdk from 'aws-cdk-lib';
import * as s3 from 'aws-cdk-lib/aws-s3';
import { Construct } from 'constructs';
import { S3Bucket } from '@aws-solutions-constructs/aws-s3-bucket';

// ------Constructs------

// -----L1 Constructs------
export class L1BucketStack extends cdk.Stack {
    constructor(scope: Construct, id: string, props?: cdk.StackProps) {
        super(scope, id, props);

        new s3.CfnBucket(this, 'MyL1Bucket',{
            bucketName: `my-l1-bucket-${this.account}`,
            versioningConfiguration: {
                status: 'Enabled',
            },
            publicAccessBlockConfiguration: {
                blockPublicAcls: true,
                blockPublicPolicy: true,
                ignorePublicAcls: true,
                restrictPublicBuckets: true
            }
        });
    }
}

// -----------------------------------------------
// -----L2 Constructs------
export class L2BucketStack extends cdk.Stack {
    constructor(scope: Construct, id: string, props?: cdk.StackProps) {
        super(scope, id, props);

        new s3.Bucket(this, `my-l2-bucket-${this.account}`, {
                    versioned: true,
                    encryption: s3.BucketEncryption.S3_MANAGED,
                    blockPublicAccess: s3.BlockPublicAccess.BLOCK_ALL,
                    removalPolicy: cdk.RemovalPolicy.DESTROY
        });
    }
}

// -------------------------------------------
// -----L3 Constructs------
export class L3BucketStack extends cdk.Stack {
    constructor(scope: Construct, id: string, props?: cdk.StackProps) {
        super(scope, id, props);

        new S3Bucket(this, 'MyL3Bucket', {
            bucketName: `my-l3-bucket-${this.account}`, 
    // This L3 construct automatically applies best practises, such as encryption, versioning, and access logging
        });
    }
}

So we will now build a [[VPC]] in [[CDK]] using [[Typescript]].
We will do what we have before, create the [[VPC]] with 2 [[AZ]]'s, each with 1 public [[Subnets]] and 1 private [[Subnets]]. By creating a private [[Subnets]], [[CDK]] will create the [[Internet Gateway]] for us. All this can be done with very little code, with thanks to [[CDK]]






# References
