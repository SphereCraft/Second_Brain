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
The public [[Subnets]] will automatically create the [[Internet Gateway]] for us. This code will create the [[VPC]] called MyVPC with 2 [[AZ]]'s (maxAzs) and in each zone will create 1 public and 1 private [[Subnets]], and finally we need to specify an output. This will show us in the terminal after our deployment what has happened.

        new cdk.CfnOutput(this, 'VpcId',{
            value: vpc.vpcId,
            description: 'VPC ID'
        })
    }
}
That is all we need to do to create the [[VPC]] stack for this example.
Now in the terminal, we need to run a few things
	npm run build - to make sure everything is good
	cdk deploy - make sure your [[AWS]] is configured in the [[CLI]]
If you get any errors, might need to bootstrap by running 
	cdk bootstrap
Once all done can run
	cdk destroy
to destroy the stack to avoid any charges.

After some debugging, mainly syntax errors, all worked fine. Seems harder, but much easier too. Destroy after and all good. There is documentation on the various imports to set things up.
 Now what does it all mean
Const VPC - constant variable, the new means we creating something new, [[EC2]] - we use this for the [[VPC]] as they work together.

MaxAzs - tell it that the maximum amount of [[AZ]]'s needed, then just naming them in [[Arrays]], public and private. The public [[Subnets]] will automatically create the [[Internet Gateway]].
PRIVATE_ISOLATED will make it private and away from any direct access to the internet.
The output is to show us in the terminal what we have just created.
This is an L2 [[CDK Constructs]], good defaults.
Clean and efficient way to code
Next the architecture will be updated.

Want to add another [[Subnets]] for each [[AZ]] for a [[Database]].
Why do it like this?
	This will give us clean separation of the resources, this is best practices.
Will now learn how to reference the [[VPC]] and how to add all the resources using [[CDK]].
With these new additions we need to update our [[VPC]].
Adding a new [[Subnets]] for the [[RDS]]
                {
                    name: 'Database',
                    subnetType: SubnetType.PRIVATE_ISOLATED,
                    cidrMask: 24
                }
 Named Database for clear identification and private to keep it secure from the internet.
 Can now deploy this and will end up having 3 [[Subnets]].
 run same command will make any additions to your code
	 cdk deploy
Now to [[Create EC2 in CDK]]









# References
