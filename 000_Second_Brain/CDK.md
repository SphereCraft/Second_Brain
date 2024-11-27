21/11/2024 1905

Status #idea

Tags:

# CDK

What is CDK?

The [AWS](./AWS.md) Cloud Development Kit is an open source software development framework for defining cloud [[IaC]] and provisioning it through [[AWS]] [[Cloudformation]].

Key features

Can use multi different code languages  with CDK, [Python](./Python.md), [Terraform](./Terraform.md), [Javascript](./Javascript.md), [Typescript](./Typescript.md) etc
It provides pre made modular pieces of code called constructs that we can use, modify and integrate to develop our infrastructure quickly.
Way more efficient to use [[Typescript]] with CDK than with [[IaC]] with [[Terraform]] and [[Cloudformation]].

[[AWS]] CDK Stacks

A stack is a unit of deployment in CDK, its a collection of one or more constructs/[[AWS]] resources that are updated, deleted as one single unit.
When we deploy a CDK Stack [[AWS]] recognises it as and [[AWS]] Stack.
Stacks will help us organise our resources
They can have stacks for different things
	Network infrastructure
	[[Database]]'s
	Application Servers
So logically better.
Stacks can also reference resources in other stacks to help build modular infrastructure.









# References
