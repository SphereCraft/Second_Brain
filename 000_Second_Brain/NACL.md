25/09/2024 0652

Status #idea

Tags:

# NACL

In [[AWS]] they act as the security check point for each [[Subnets]] within the [[VPC]], they monitor and regulate the traffic coming in and out of the [[Subnets]]. They check every [[Data  packets]] to see if it matches the rules to allow access or not. Unlike [[Security Groups]], NACL's are not [[Stateful]], they are [[Stateless]]. So everything in or out is checked. If a rule is set for inbound a rule needs to be set for inbound as [[Data  packets]] are not remembered.
The [[Security Groups]] will protect the instance within the subnet and the NACL's will protect the [[Subnets]]. This gives and extra layer of protection at the [[Subnets]] level.
# References
