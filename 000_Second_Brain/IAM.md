26/09/2024 0704

Status #idea

Tags:

# IAM

***Identity Access Management***

This is a function that is often overlooked in [[AWS]]
This service allows you to control, under certain conditions, access to [[AWS]] resources. You can make groups/users and give them permissions giving them access or not to the services ([[AWS]] resources). IAM is critical part of [[AWS]] providing the security to manage and access the data and resources. IAM is essential in managing cloud resources securely for several reasons.
	[[Access Control Management]]
	[[Principle of Least Privilege]]
	[[MFA - Multi-Factor Authentication]]
	[[Secure Application Operation]]
	[[Integration and Federation]]
An IAM user is an identity created in [[AWS]] that represents a person of service that interacts with [[AWS]]. IAM can be anyone or app or service that needs to interact with [[AWS]].
Creating a new user via the console
Go to IAM dashboard - click users - create new
give name - give required access to relevant things required for their job role.
set auto password, but allow them to set new password on next login
can then go back to users and see what permissions are set, before you could send all details direct to their email.

Best practices
	principle of least privilege
Only give the user enough privilege so they can do they job role - no more!
Can create Groups for users and give the group the permissions then place the user in that group for the permissions.
				***Only give access to what they need!!!***
Should always review and rotate privileges and passwords every 60-90 Days.




# References
