25/11/2024 0506

Status #idea

Tags:

# Create VPC in CDK

import * ec2 from 'aws-cdk-lib/aws-ec2'
import * as cdk from 'aws-cdk-lib';
import { Construct } from 'constructs';
import * as ec2 from 'aws-cdk-lib/aws-ec2'

export class VpcCdkProjectStack extends cdk.Stack {
    constructor(scope: Construct, id: string, props?: cdk.StackProps) {
        super(scope, id, props);


        const vpc = new ec2.Vpc(this, 'MyVpc', {
            maxAzs: 2,
            subnetConfiguration: [
                {
                    name: 'Public',
                    subnetType: ec2.SubnetType.PUBLIC,
                    cidrMask: 24
                },
                {
                    name: 'Private',
                    subnetType: ec2.SubnetType.PRIVATE_ISOLATED,
                    cidrMask: 24
                },
The public [Subnets](./Subnets.md) will automatically create the [Internet Gateway](./Internet_Gateway.md) for us. 
This code will create the [VPC](./VPC.md) called MyVPC with 2 [AZ](./AZ.md)'s (maxAzs) and in each zone will create
1 public and 1 private [Subnets](./Subnets.md), and finally we need to specify an output. This will show us in the 
terminal after our deployment what has happened.

        new cdk.CfnOutput(this, 'VpcId',{
            value: vpc.vpcId,
            description: 'VPC ID'
        })
    }
}
That is all we need to do to create the [VPC](./VPC.md) stack for this example.
Now in the terminal, we need to run a few things
	npm run build - to make sure everything is good
	cdk deploy - make sure your [AWS](./AWS.md) is configured in the [CLI]
If you get any errors, might need to bootstrap by running 
	cdk bootstrap
Once all done can run
	cdk destroy
to destroy the stack to avoid any charges.

After some debugging, mainly syntax errors, all worked fine. Seems harder, but much easier too.
Destroy after and all good. There is documentation on the various imports to set things up.
Now what does it all mean
Const VPC - constant variable, the new means we creating something new, [EC2](./EC2.md) - we use
this for the [VPC](./VPC.md) as they work together.

MaxAzs - tell it that the maximum amount of [AZ](./AZ.md)'s needed, then just naming them in 
[Arrays], public and private. The public [Subnets](./Subnets.md) will automatically create the [Internet Gateway](./Internet_Gateway.md).
PRIVATE_ISOLATED will make it private and away from any direct access to the internet.
The output is to show us in the terminal what we have just created.
This is an L2 [CDK Constructs](./CDK_Constructs.md), good defaults.
Clean and efficient way to code
Next the architecture will be updated.

Want to add another [Subnets](./Subnets.md) for each [AZ](./AZ.md) for a [Database](./Database.md).
Why do it like this?
	This will give us clean separation of the resources, this is best practices.
Will now learn how to reference the [VPC](./VPC.md) and how to add all the resources using [CDK](./CDK.md).
With these new additions we need to update our [VPC](./VPC.md).
Adding a new [Subnets](./Subnets.md) for the [RDS](./RDS.md)
                {
                    name: 'Database',
                    subnetType: SubnetType.PRIVATE_ISOLATED,
                    cidrMask: 24
                }
 Named Database for clear identification and private to keep it secure from the internet.
 Can now deploy this and will end up having 3 [Subnets](./Subnets.md).
 run same command will make any additions to your code
	 cdk deploy
Now to [Create EC2 in CDK](./Create_EC2_in_CDK.md)









# References
