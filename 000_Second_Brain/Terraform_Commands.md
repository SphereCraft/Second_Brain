01/11/2024 2033

Status #idea

Tags:

# Terraform Commands

Primary [[Terraform]] Commands

[[Terraform]] init
This initialises a new or existing [[Terraform]] configuration, it will download the necessary provider plugins and set up the [[Back End]] for storing state files.
Should use it after creating a new configuration or when you've added a new provider to an existing configuration.

[[Terraform]] Plan
This creates an execution plan and compares the current state with the desired state defined in your configuration
	Determines what actions need to be taken to achieve that desired state.
The plan will show you the changes that [[Terraform]] will make to your infrastructure before you apply them

[[Terraform]] apply
After reviewing the plan you can apply the changes to your infrastructure. This command executes the actions proposed in the plan creating, modifying or deleting resources as needed.
This is the same as the aws cloudformation deploy command

[[Terraform]] show
This command displays the current state of your infrastructure resource in a human-readable format.
Useful for inspecting your infrastructure's configuration nad understanding the relationship's between resources.
Same as using aws cloudformation describe command

[[Terraform]] output
If you've defined output values in your configuration, you can use this to retrieve the value of those outputs.
Useful for retrieving information about your infrastructure, such as
[[IP Address]]
Resource ID's
Metadata

[[Terraform]] destroy
When ready to tare down your configuration, use this command. It will remove all resources managed by your configuration. This command will prompt you confirmation before executing. Similar to aws cloudformation delete command

[[Terraform]] fmt
This will automatically formats your [[Terraform]] configuration files according to the canonical style conventions. It helps maintain consistent formatting across your codebase, making it easier to read and collaborate on.
There is no cloudformation alternative command.

[[Terraform]] validate
This checks the syntax of your [[Terraform]] configuration files and ensures that they are properly formatted. Useful to catch and errors/issues before applying changes.

[[Terraform]] follows this consistent pattern
		Plan - terraform plan to review changes
		Apply - terraform apply to execute changes
		Observe - terraform show or terraform output to observe the infrastructure state.








# References
