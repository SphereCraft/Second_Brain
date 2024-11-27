18/11/2024 1003

Status #idea

Tags:

# Lists

List are important in cloud engineering. A list is an ordered collection of items, they can be strings, variables or even other lists.
Lists are great for managing resources.

'# List of EC2 instances'
instance_ids =["i-1234", "i-5678", "i-9012"]

'#List of IP Addresses'
ip_addresses = ["10.0.0.1", "i-10.0.0.2", "i-10.0.0.3"]

'# List of Availability Zones'
availability_zones = ["eu-west-1a", "eu-west-1b", "eu-west-1c"]

'# Print Lists'
print(f"EC2 Instance to terminate {instance_ids}")
print(f"EC2 Instance to terminate {ip_addresses}")
print(f"EC2 Instance to terminate {availability_zones}")

To add to a list we use the append method

'# Add new EC2 Instance ID' 
instance_ids.append("i-3456")
print("After adding a new Instance ID")
print(f"EC2 Instances:  {instance_ids}")

To remove an item from the list we will use the remove method. This is useful if, lets say, an EC2 instance has be terminated.

'# [[Remove method]] and EC2 Instance'
instance_ids.remove("i-1234")
print("After removing an Instance")
print(f"EC2 Instance: {instance_ids}")
(can also use print("EC2 Instance: " instance_ids)), but try to be consistent and use f strings when adding integers or other variables to a string. refer to [[f string]]

'# [[Check method]] if an item is in a list'
if "10.0.0.4" in ip_addresses:
    print("Yes 10.0.0.4 is in and allowed")
else:
    print("No, 10.0.0.4 is not in the allowed list")
print(f"IP addresses , {ip_addresses}")

[[Slice method]] and [[Sort method]]
Slicing allows you to get a portion of a list. Useful when you only need to work with a small part of a list

'# Slicing a list'
'# First two AZs 
first_two_azs = availability_zones[:2]
print(f"First two AZs: {first_two_azs}")

the [:2] will return the first 2 items in the list.

[[Sorting Method]]
Sorting a list with the sort method will sort the list in ascending order.

'# Sorting a list' 
instance_ids.sort()
print(f"Sorted EC2 Instances: {instance_ids}")

[[Length method]]
We can find the length of a list using the [[Length method]]
'# Length Method
'# Finding the length of a list 
number_of_ips = len(ip_addresses)
print(f"Number of IP Addresses: {number_of_ips}")

[[Indexing method]]
We can also access list items via the [[Indexing method]]. Index start at zero and can even count backwards from the last item that starts at -1

'# Accessing list of items by Index
first_az = availability_zones[0]
last_az = availability_zones[-1] # indexing will count backwards, so -1 is last, -2 is second to last
print(f"First AZ: {first_az}")
print(f"Last AZ: {last_az}")

[[Dictionaries]]
These are integral to AWS







# References
