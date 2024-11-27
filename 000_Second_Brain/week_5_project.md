03/10/2024 0716

Status #idea

Tags:

# week 5 project


![[cbb2ce2-47d0-4ed7-efdf-fb86a6a458_Screenshot_2024-03-05_at_22.webp]]

0.0.0.0/0 denotes all possible IP addresses
So Public Subnets destination is 0.0.0.0/0 which denotes all possible [[IP Address]], these will be targeted through the [[IGW]].
There is also a connection to all the Local subnets within the [[VPC]] with the IP address of 10.0.0.0/16
The App Subnet (private) connection for all possible [[IP Address]] will be via the [[NAT Gateway]], then on to the [[IGW]] if access to the internet is required.
The Database (private) Subnet only have one connection and that's the local connection (10.0.0.0/16) which will go via the app subnet then onto the [[NAT Gateway]] and on to the internet that way. This is to give an extra layer of security, so our subnets can have access to the internet for update etc, but outside traffic can be stopped entering the [[NAT Gateway]]
![[week5 project.png]]
Its important to remember the ideal route for all traffic. The [[NAT Gateway]] is an added layer of security.
Make sure the traffic is routed through the correct [[AZ]], do not want to have cross routing.
[[NAT Gateway]] are charged on an hourly basis and data usage, so we will create a [[VPC]] but will not add the [[NAT Gateway]] yet.
Now [[Create VPC]]

***Setting up a Bastion Host***

in this part we are going to set up a bastion host via ssh to connect to [[EC2]] in AV1 then ping [[EC2]] in AV2, changing security and many other part. This should get us used to setting rules and other parts. We are doing this instead of using a [[NAT Gateway]] due to the cost implications.

Start by setting up an [[EC2]] instance

Go to [[EC2]] dashboard
Launch instance
Name instance (BastionHost)
Key Pair - create new
name as bastion
RSA
this will create and download, remember where it is
Network Settings - Edit
Select correct [[VPC]]
Select correct [[Subnets]] (go back and rename to find easier)
select PublicSubnet2a
Enable Auto Assign Public IP
Change Security Group Name (bastionSG)

Inbound Rules
Type - ssh
Protocol - TCP
Port Range - 22
Source type - My IP - your IP will be displayed
Description - MyLocalIP

Launch Instance


# References
