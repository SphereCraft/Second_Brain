202407271513

Status #idea

Tags:

# Server-Less Architecture

[[Server]]-less architecture is a cloud application deployment model. where the cloud provider dynamically manages the allocation and provisioning of servers.A [[server]]-less application runs in a state less compute container that are event triggered and fully managed by the cloud provider. Everything from the patching, scaling and provisioning is managed by the cloud provider.
Its called [[server]]-less, not because there are no servers, but because the developers don't have to own, rent or manage them so they can write code and deploying without worrying about the underlying infrastructure 

![[serverless.png]]
[[server]]-less architecture looks very similar to microservices, but its very different.
- users - user app is a web app either on PC, mobile or any other device
- API Gateway is the single point that is reasonable for routing the request from the user to the correct [[server]]-less function based on the API end point that the request is intended for
- [[Server]]-less function  - they will preform they own specific task depending on what has been assigned.
- Database - will handle all the persistent data needed and will be connected to the data function and sometimes others functions. the database can be a managed database

Remember - in [[server]]-less architecture there are no long running servers to manage, instead the cloud provider dynamically manages the invocation and execution of these functions to a response like an HTTP request. This means you only pay for the execution of a request.
Server-less architecture supports scalability out of the box, as more users interact with the web app the architecture with automatically add more instances of the functions required. this is done without any manual intervention required, insuring the application can handle high traffic without any decrease in performance

![[serverless vs microservices.png]]

Server-less
- Managed by cloud provider
- active when triggered
- scaled automatically
- pay when being used

Microservices
- Independently managed
- Always on
- Each service is managed independently


---
# References
