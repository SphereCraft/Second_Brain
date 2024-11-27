22/11/2024 0640

Status #idea

Tags:

# New CDK Project

// Typescript

let bucketName: string = 'my-bucket';
let maxItems: number = 100;
let isPublic: boolean = false
let tags: string[] = ['project:cdk', 'env:dev'];

// Typescript Interface

interface MyBucketProps {
    bucketName: string;
    versioned: boolean;
    encryption: s3.BucketEncryption;
}

Top is examples of data types.
Interface describes the structure of an object.

    const bucketProps: MyBucketProps = {
        bucketName: 'My-S3-Bucket-JJ-CDK-' + this.account,
        versioned: true,
        encryption: s3.BucketEncryption.S3_MANAGED,
    }

        new s3.Bucket(this, 'MyFirstBucket', bucketProps)
  }
 here we have created a new bucketProps that follows MyBucketProps. We used this account to get the current AWS account number to ensure the bucket name is globally unique.
 Versioned and encryption have to add these too
 Then add a new [[S3]].bucket using the [[S3]] bucket construct. Then it creates 'MyFirstBucket'








# References
