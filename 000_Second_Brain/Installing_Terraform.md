01/11/2024 1750

Status #idea

Tags:

# Installing Terraform

Installing Terraform is different for each platform, but luckily on Arch Linux its part of the package, so just need to do this command

sudo pacman -S terraform
then terraform --version to check that its up to date
But in VSCode i had top add the expansion for it, on left side click icon for expansion, then search for terraform, top one install. This should give you the coloured highlighted syntax to help.

Now create a new folder called terraform all within the same set of folders as that's where the git repository is located (could change later if needed, but as learning keep it this way). Then create a new file call main.tf (tf is the extension for terraform files)
So will create the AWS provider and add local region

provider "aws" {
	region = "eu-west-2" (this needs to be your local region)
}

Then in terminal make sure you are in the new directory, then in terminal
terraform init
this will apply all the plugins needed.




# References
