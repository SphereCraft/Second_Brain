03/11/2024 1656

Status #idea

Tags:

# Create VPC in Terraform

So to start building a [[VPC]] - continue in the main.tf file.
'# VPC'
resource "aws_vpc" "(name)main" {
	cidr_block = "192.168.0.0/16"
	tags = {
		Name = "main-tf-vpc"
		}
}

then create the subnets

'# Subnet 1'
resource "aws_subnet" "subnet1" {
	vpc_id = "aws_vpc.main.id"
	cidr_block = "192.168.1.0/24"
	availability_zone = "eu-west-2a"
	tags = {
		Name = "subnet1"
		}
}

Make subnet 2 the same but replace the relevant details with 2 and b, and make the cidr block 1 different.
Now the internet gateway

'# Internet Gateway'
resource "aws_internet_gateway" "igw" {
	vpc_id = aws_vpc.main_id
	tags = {
		Name = "main-vpc-igw"
		}
}

Now root table

'# Root Table'
resource "aws_route_table" "route_table" {
	vpc_id =aws_vpc.main.id
	route {
		cidr_block = "0.0.0.0/24"
		gateway_id = aws_internet_gateway.igw.id
		tags = {
			Name = "main_route_table"
			}
		}
}

Then the root table association subnets 1 and 2

'# Route table association Subnet 1'
resource = "aws_route_table_association" "a" {
	subnet_id = aws_subnet.subnet1.id
	route_table_id = aws_route_table.route_table.id
}

'#Route table association Subnet 2'
resource = "aws_route_table_association" "b" {
	subnet_id = aws_subnet.subnet2.id
	route_table_id = aws_route_table.route_table.id
}

Now during the deployment of this code you will see errors
terraform init
terraform plan
So the error should be because the terraform state file isn't locked
Run aws s3 ls to check that the files are there, to check the dynamodb run
aws dynamodb describe-table --table-name s3-tf-table
this should show all the detail (think i need to make sure my aws is linked to VSCode correctly).
So in the console we will make a new dynamodb
aws dynamodb create-table --table-name terraform-lock-file \
--attribute-definitions AttributeName=LockID,AttributeType=S \
--key-schema AttributeName=LockID,KeyType=HASH \
--provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1
To do this in the console, i think, if you replace the partition key with LockID, i think this will do the same thing.
This should create a new table so need to change the table name in the state file.
Check for any error in the code, VSCode with the extension is great for helping with this.
Because we have changed the lock file we need to update the state, so run
terraform init -migrate-state
then do 
terraform plan
should now see everything that is planned to be deployed, check that everything is there, this is good practice, when happy
terraform apply
follow prompts
everything should happen now.
Validate in aws console, when happy go back to console and destroy all
terraform destroy







# References
