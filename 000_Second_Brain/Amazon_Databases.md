31/10/2024 2106

Status #idea

Tags:

# Amazon Databases

Amazon has a number of databases, the 2 main ones are 
	- RDS - Relational
	- Dynamo DB - Non Relational
In a relational database the data is organised into tables where the data is related to each other, like book and there title, author etc.
Non Relational (AKA NoSQL) is more free form like a JSON file and no organisation, like all data for one book is together.

RDS in [AWS](~/Documents/Second_Brain/000_Second_Brain/AWS.md) the provisioning, configuration, patching and back ups are all automated. 
RDS is built on top of an [EC2](~/Documents/Second_Brain/000_Second_Brain/EC2.md).
Benefits of RDS
	Multi [AZ](~/Documents/Second_Brain/000_Second_Brain/AZ.md) - Improved reliability
	Automatic Fail over - if one fails, it automatically moves to a new [AZ](~/Documents/Second_Brain/000_Second_Brain/AZ.md)
	Read Replicas - helpful for disaster recovery, can put our read replica in a different region.
	Automatic Backups - scheduled period, once a day
	Includes RDS instance, Transaction logs and there is a retention period of up to 35 days, any long and can store the back up in an S3.





# References
