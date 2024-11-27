31/10/2024 2115

Status #idea

Tags:

# Create an RDS in IaC

VScode, create new file rds.yaml
Usual start

AWSTemplateFormatVersion: '2010-09-09'
Description: 'Create RDS Instance'

Resources: 

	'# My Database'
	MyDB:
		Type: 'AWS::RDS::DBInstance'
		Properties:
			DBInstanceIdentifier: 'MyNewRDS'
			MasterUsername: 'admin'
			MasterUserPasswor: 'password' (never normally do this, this is just example)
			DBInstanceClass: 'db.t3.micro'
			Engine: 'mysql'
			EngineVersion: '8.0.35'
			AllocatedStorage: '20' (in GiB)
			BackupRetentionPeriod: 7

Can now deploy this in the usual way using create-stack, when deployed can validate in the console like normal to check all setting we added are visible. After its been create, delete it to save getting charged.
Now, i think we will be putting it all together and building a complete architecture where it all integrates with each other.




# References
