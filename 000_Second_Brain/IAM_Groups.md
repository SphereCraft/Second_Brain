21/10/2024 2142

Status #idea

Tags:

# IAM Groups

IAM Groups are so you can create a group policy and add multiple users to the group so they will all have the same access. ie a group of developers with the same privileges.
This help to make things easier to manage and control, ie if someone leaves the business and another replaces them, they can be removed and add without having to worry about what policies they need.
There are so many different policies that can be attached to either an individual or group to fine grade each persons role/access within the business.
There are
	Managed Policies - These are made and managed by [[AWS]].
	In Line Policies - These we create and manage for individual users.
	Custom Policies - These we create and select all actions to suit the need, giving more flexibility.
Stay away from in-line, either use [[AWS]] managed policies or make your own custom policies.

Create policies, then can select actions to suit and attach conditions.
Next - policy name etc.


# References
