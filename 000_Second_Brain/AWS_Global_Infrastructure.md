16/09/2024 0645

Status #idea

Tags:

# AWS Global Infrastructure

AWS services are like a global power grid
AWS Regions are like a global network of power stations servicing independant global areas, so if there's a problem in one region then it wont't effect any others, this will help keep things going within the network and isolate the area effected.
Each region is a cluster of data centers with multiple zones (like power generators) known as [[AZ]]'s
Each [[AZ]] has its own data centre with its own redundant power, networking and connectivity designed to insure services run smoothly, even if there are issues.
Each [[AZ]] are at least 60 miles apart from each other for better fault tolerance and stability.
There are then Local Zones, these extend from the main AZ's and bring the services closer to the user.
Local zones are designed for latency sensitive applications ensuring the user has fast and reliable access to core AWS services without the lag that distance can have.
Next is Edge Locations, these are used to cache data closer to users for even lower latency supporting services like Amazon [[Cloud Front]]. They are the last mile of the system.
When logging into the AWS dashboard, not all services are available in all regions straight away depending on the roll out status
AWS services are a vast and highly efficient network making sure, and designed, so computing resources are always available.
Understanding how [[Regions]], [[AZ]]'s, [[Local Zones]] and [[Edge Locations]] work together you can design a system that is resilient, fast, scaleable and meets users needs no matter where they are in the world.
# References
