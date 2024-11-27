31/07/2024 0656

Status #idea

Tags:

# EC2

Amazon Elastic Cloud Compute (EC2) is a cloud based, on demand virtual server service that is scalable to meet your needs, as many or as few servers as required depending on what is required

"An EC2 instance is a virtual server in the AWS Cloud. When you launch an EC2 instance, the instance type that you specify determines the hardware available to your instance. Each instance type offers a different balance of compute, memory, network, and storage resources. For more information, see the [Amazon EC2 Instance Types Guide](https://docs.aws.amazon.com/ec2/latest/instancetypes/)."

[[Setting up EC2]] is a simple process following a few prompts and menus

EC2 is re-sizeable compute capacity in the cloud that offers many different services depending on the use case required from the business
	CPU -Memory-Storage-GPU etc
	Easily scalability up or down
	Cost Effective, only pay for what you use
	Flexibility - operating systems, instance types and configurations
and its built on AWS's proven and reliable infrastructure.

***EC2 categories of instance types***

*General Purpose*
Suitable for Web Servers
		   Development Environments
		   Small to medium Databases

*Compute Optimised*
	Designed for high workloads that require high processing power
	Ideal for
		Batch Processing
		High-Performance computing
		Scientific Modelling
		
*Memory Optimised*
	Large amount of memory
Ideal for 
	High performance databases
	In-Memory databases
	Big data analytics

*Storage Optimised*
	High performance systems
	Ideal for 
		Distributed file systems
		data warehousing
		Log processing
Fast and efficient, Local SSD Storage, High Bandwidth network connectivity.

*Accelerated Computing*
	Equipped with hardware accelerators like
		GPU's
		FPGA's - Field Programmable Gate Array's
	to accelerate workflows
	Ideal for
		Machine Learning
		Scientific Simulators
		3D Rendering

Each instance type will have many different types to suit all needs.

**Naming convention for EC2 instance types**
Prefix - instance family

t - Burstable
m - General Purpose
c - Compute Optimised
Followed by a number indicating the generation and size modifier, ie large, xlarge and 2xlarge.
Choosing the right instance type will be determined by workload requirements, performance needs and budget.
Consider the following factors
	CPU
	Memory
	Storage
	Network Bandwidth
	Hardware needs
AWS often introduces new versions, so keep checking and don't stick to the same old ways.
**EC2 pricing models**
	*On-demand instances* - ideal for short term, spiky or unpredictable workloads
	*Reserve instances* - Low price but commitment of 1-3 years, Ideal for Steady state/predictable workloads.
	*Spot Instances* - These allow to bid on unused EC2 capacity, prices fluctuate depending on supply and demand. Theses could be cost saving, but could be interrupted if spot price exceeds your bid.
	
Various processor options can include
	intel Processors
	AMD Processors
	NVIDIA GPU's
	AWS Graviton
Choose what suits the needs.Understanding the workload requirements and match the instances needed.
Understand the nature of your application or project
	is it a website, compute intense application or a memory hungry database.
ie a simple web application might only need a t2.micro or t3.small EC2, these give a balance of CPU, memory and network resources, ideal for lightweight web serving, small databases

Machine learning might need power CPU and lots of memory, so something from the compute optimised like c5.4xlarge.

In-memory database like Redis, choose an instance from memory optimised like r5.xlarge. Hugh memory, high memory bandwidth.

Available instance sizes range from 
	micro to 32xlarge
Monitoring the application resources overtime. Amazon [[Cloudwatch]] can help watch CPU Memory and network usage for any bottle necks.
Process - Start with and educated guess based on workload requirements, then monitor and adjust if needed.



# References

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html