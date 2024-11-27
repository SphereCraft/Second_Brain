=[;01/11/2024 1759

Status #idea

Tags:

# Terraform providers and plugins

What are terraform providers?
They are plugins that terraform users to interact with remote systems and [[API]]'s. Each provider has a set of resource types and data sources that terraform can manage.

Key Concepts

Provider configuration
The purpose of provide configuration is to set up
	Authentication Credentials
	Region Settings
	Provider specific configurations
For all the things associated with that provider.
ie
aws - Access keys - Default Region - Profile Name

Resource Management
Providers define and implement specific resource types ie aws_instance, similar to specifying the type of service we are going to use with [[Cloudformation]]
Resources have various attributes that you can configure with Terraform Configurations.
These are like the properties in [[AWS CloudFormation]]
Data Sources
In addition to resources, providers can offer data sources, these allow Terraform configuration from outside

How do providers work?
When you define a provider in your [[Terraform]] configuration, [[Terraform]] will automatically download and install the relevant required provider plugins during the [[Terraform]] init process. This will make sure everything is up to date and compatible with the [[Terraform]] core
[[Terraform]] keeps a registry of official and community contributed providers.
Example of configuring a provider in [[Terraform]]

provider "aws" {
	region = "eu-west-2"
	access_key = "my-access-key"
	secretkey = "my-secret-key"
}

Provider is AWS and region specifies the [[AWS]] region where resources will be created. Access and secret key are the authentication credentials for accessing [[AWS]]

Then can start defining resources provided by the supplier, for example

resource "aws_instance" "example" {
	ami = "ami-0000"
	instance_type = "t2.micro"
}

This configuration creates an [[AWS]] [[EC2]] instance using [[AWS]] provider

Managing Multiple providers

You can configure multiple providers within a single [[Terraform]] configuration. This is useful for managing resources across different cloud platforms or even different regions within the same provider.
In this next example there is 2 different regions configured within [[AWS]]

provider "aws" {
	alias = "west"
	region = "us-west-1"
}
provider "aws" {
	alias = "east"
	region "us-east-1"
}
resource "aws_instance" "example_west" {
	provider = aws.west
	'# Configuration for the instance'
}
resource "aws_instance" "example_east" {
	provider = aws.east
	'#Configuration for the instance'
}

Understanding [[Terraform]] providers is fundamental to using [[Terraform]] effectively
Providers allow [[Terraform]] to work with a diverse set of infrastructure technologies making it very powerful.




# References
