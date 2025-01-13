23/10/2024 0720

Status #idea

Tags:

# Auto Scaling Groups

Auto Scaling Groups is a group of [EC2](~/Documents/Second_Brain/000_Second_Brain/EC2.md) instances that share similar characteristics and are
treated as a logical grouping for scaling and management. When setting up a group, we define a minimum and maximum number of instances allowing 
[AWS](~/Documents/Second_Brain/000_Second_Brain/AWS.md) to scale between these 2 numbers.

Launch Configurations/Templates
This is a template that Auto scaling groups will use to launch new [EC2](~/Documents/Second_Brain/000_Second_Brain/EC2.md) instances. These include
configurations like
	- Instance types
	- AMD ID
	- Key Pairs
	- Security Groups
	- Associated Block Storage
[AWS](~/Documents/Second_Brain/000_Second_Brain/AWS.md) launch templates provide greater flexibility and more features, they also allow for different 
instance configurations under the same template ID.


# References
