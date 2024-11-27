23/08/2024 0647

Status #idea

Tags:

# Application Delivery Controller

An application delivery controller (ADC) is a purpose-built networking appliance used to improve the performance, security, and resiliency of applications delivered over the web.
##### How does an application delivery controller work?

An application delivery controller employs algorithms and policies to determine how inbound application traffic is distributed. Round robin, which forwards client requests to each server in turn, is a fairly rudimentary form of [[load balancing]]. This method assumes all servers are the same: It does not take into account health or responsiveness. An administrator can implement additional policies that direct an ADC to check for a number of criteria before determining to which server an inbound request should be sent. The application delivery controller can inspect packet headers for keywords or requested file types and direct the request to the appropriate server based on this information.

Application delivery controllers are also heavily relied upon for their monitoring capabilities. They can check a server’s health and operability beyond the standard ping. If monitoring indicates a server is experiencing an issue, or that specific health criteria needed to ensure a server’s reliability are not being met, the ADC will route traffic to an alternate server, avoiding a potential disruption.

Application delivery controllers can also provide real-time and historical analysis of all user and network traffic, including metrics for round-trip times, bandwidth usage, and datacenter and wide area network (WAN) latency. This information can assist help desk staff by minimizing the time they spend identifying the cause of an issue and help users by providing faster resolution.
# References

https://www.netscaler.com/articles/what-is-an-application-delivery-controller