15/08/2024 2156

Status #idea

Tags:

# Load Balancing

**Load balancing**

this is used to protect the servers from overloading

user requests get sent through the load balancer and will decide which [[server]] to use and will balance the amount of requests to keep the servers even and can also increase the amount needed

##### Importance
Reduces downtime, improves performance, scalability

load balancing has session persistence, sometimes is important to keep users on the same back end [[server]] for the duration of their interaction, load balancers can help with this because they can be configured to maintain a session state even through sticky sessions or session infinity techniques.

And they can check the health of the servers (virtual), and if a [[server]] is down they will re direct to a different [[server]] to maintain the performance to keep the user running.

They can also offload the ssl encryption from the back end servers, which means they can handle the encryption and decryption for the HTTPS, this will reduce the workload on the back end servers making the whole operation more efficient.

**High availability**
high availability is all about operational performance, making sure our system is always up and running. In a simple way, its all about up time. Its makes sure our system is constantly active and interrupted.

The users are making requests to a service via the internet, and these user expect to access the service at anytime, day or night, without interruptions without issues.

The internet is the medium which send the request to access the service provided by the back end systems.

Then the load balancer, the most critical component for achieving high availability. The load balancer will distribute the in coming requests across the cluster of virtual servers, which will balance the load to prevent any [[server]] from becoming overwhelmed, but also ensures that if one fails another can pick up the workload, therefore it maintains the availability of the service

Finally the high availability cluster, the group of servers which are configured to work together to provide continues service and will be configured that if one fail the workload can be spread across the others. Key aspect of High Ava

Fail-over – load balancer
health checks – between load balancer and cluster
redundancy

Load balancers can also offer [[Caching]], [[Traffic shaping]] and [[compression]] which is part of the ADC ([[Application Delivery Controller]])

**How they work**
They get a request and will route the request to the least busy or closest (geographically) based on algorithms. eg [[round robin]] which can give it greater availability etc.

**Load balancers are focused on sending the traffic distribution** 
# References
