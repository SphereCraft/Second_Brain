20240730 0651

Status #idea

Tags:

# Block Storage

Block storage splits the data in to uniform blocks of data each with its own unique identifier which is then stored in a [[SAN]]. These blocks can be combined together to form larger Blocks when needed for higher input/output demands.

Best use of Block Storage 
- When there is a need for high input/output of databases and transactional data.
- When running virtual machines or containers that require a file system
- For application that require raw, unformatted storage that can be managed by the operating system like it was a physical hard drive.

#### Advantages
-  High performance
- Low latency
- control of storage - each block can be controlled like an individual hard drive

#### Disadvatages
-  More expensive than [[File Storage]] or [[object storage]]
- Less scalable when looking at capacity and management
- requires more management and overhead to scale out

##### example
AWS - Amazon [[EBS]]

# References

https://cloudengineeracademy.mykajabi.com/products/cloud-academy-tech-with-soleyman/categories/2154687876/posts/2174972391