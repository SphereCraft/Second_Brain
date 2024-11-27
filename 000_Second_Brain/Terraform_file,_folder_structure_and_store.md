02/11/2024 0945

Status #idea

Tags:

# Terraform file, folder structure and store

Use modules for re usability, this promotes the principle of ***DRY***
***Do not
Repeat
Yourself***

In other words, to prevent repeating code across your configuration, make repeatable block and references.
Keeping modules in separate folders, keeping things clean will help organise things in a better way.
So to start make a new folder in the terraform folder and call it terraform_root_folder for this example. This is the root folder. Then create a module folders in the root folder/directory. Then each module should have it's own directory too, so add directories network, compute and in each of those add files main.tf variables.tf outputs.tf
Even in other directories like database etc, you should have the same 3 file names.
Can also have production, staging and development. This organising can help prevent and accidental changes. This is also important for deploying and changes safely.
Will have a different directory for every environment which will have the same 3 main files, main.tf variables.tf outputs.tf
So inside the root folder add folders environments, production, staging and development.
Add the 3 main file to each new folder.
Another best practice is to use consistent naming for files and resources and name things simply and relevant. (Be anal).
Keep state files separate. We will use remote state file and store in an [[S3]], doing this will help when working in a team, so we all have access to making changes etc.
This will help prevent and conflicts.
Right now Terraform will store the state files locally, but what we want to do is store it remotely, in an [[S3]] with a [[DynmoDB]]
So create a state file in root folder and call it state.tf
Then define the [[terraform]] [[Back End]]

terraform {
	backend = "s3" {
		bucket = "my-terraform-state" (or whatever you have called the bucket)
		key = "global/s3/terraform.tfstate"
		region = "eu-west-2"
		dynamodb_table = "s3-tf-table" (or whatever the root table is called)
		}
}

This block is a top level block to define what the sate [[Terraform]] file will be saved.
[[Back End]] specifies what the backend will be, in this example we choose an [[S3]] bucket.
Bucket is the name given (globally unique)
Key = path within the [[S3]] bucket where the state file will be stored
region is your region
dynamodb_table is use for the state locking. [[Terraform]] uses this to lock the file during operation to prevent and concurrent changes within the team.
Why use a remote backend
better collaboration
security - this is very sensitive information
state locking
recovery

Before we can run this state file [[S3]] configuration, we have to [[Create S3 Bucket in IaC]] or in the console. Need to make sure the names all match up when creating the [[S3]] bucket and dynamodb table. Doing this in the console this time (mistakes are made, so watch for a change later). So back to the console, create a table, and partition key called tf (this bit is wrong, look later).

Back to VSCode in root folder create a new main.tf with provider details

provider "aws" {
	region = "eu-west-2"
}

try to deploy it. (it will fail)
terraform init first, this should get everything initialised
Should show the the [[S3]] has been set up, So the state from now onwards is stored remotely.

[[Terraform]] also has documentation for all information as in the cloudformation docs. So and details needed will find here. Just search terraform docs aws and everything is explained on how to code the resource, very informative.









# References
