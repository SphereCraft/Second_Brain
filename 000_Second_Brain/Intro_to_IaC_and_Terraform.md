01/11/2024 0628

Status #idea

Tags:

# Intro to IaC and Terraform

Infrastructure as Code (IaC) - Key DevOps Practice that involves managing and provisioning infrastructure resources with machine-readable definition files rather than manual configuration with interactive tools, such as AWS Console.
The core principle of IaC is to treat your infrastructure ([[networks]],]] [[virtual machines]], [[databases]], [[load balancers]]) as software code, which eliminates manual configuration, which allows infrastructure deployment to be more consistent and repeatable.
*Benefits of IaC*
	Consistency and Accuracy
	Minimises human errors
	IaC configuration scripts ensures it used every time, which reduces configuration drift and ensures consistency.
	Speed and Simplicity - Can be rapidly set up and torn down - allows for quick testing, development and deployment cycles. Time to market and agile workflows
	Version Control.
	Infrastructure changes - commits, versioned and tracked
	Allows for Audit changes
	Revert to previous versions
	Manage infrastructure changes
This is why we need tools like [[Terraform]], which gives us the ability to build, make changes and version controls safely and efficiently across all networks using [[HCL]].

**Key Features of [[Terraform]]**
	*Declarative Approach*
		As the user, you can say how the infrastructure should be and [[Terraform]] will do the HOW.
	*Cloud Agnostic*
		Meaning, can use across the 3 main platforms, AWS, Azure and GCP, whereas cloudformation only works with aws.
	*CLI Outputs*

By using [[Terraform]] and [[IaC]] we can be
	Consistency and reproducible
	Collaboration and version control
	Automated provisioning
	Dependency management
	Cost optimisation
	Scalability
We will learn to use [[Terraform]] and [[IaC]] to streamline our AWS infrastructure.





# References
