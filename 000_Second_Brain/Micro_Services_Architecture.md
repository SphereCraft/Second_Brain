202407271509

Status #idea

Tags:

# Micro Services Architecture

Micro services Architecture is a method of developing software systems focusing on building a collection of small independent service units. In each of these microservices they are a self contained piece of business functionality and operates autonomously

3 Layers
- User interface, the front end, the part that the user interacts with
- microservices, the area where it interacts with all the services requested by the users input and are separate from each other, so these can be scaled and updated independently from each other.
- database, each microservices has its own independent dedicated database, which allows independent loose coupling, so can be scaled individually.
This all mean that each microservice will not impact each other, so scaling and updating can be done on just the specific service and in turn can be deployed quicker.It is then also possible to have a different team members to work on different sections.

**API Gateway manages requests between the client and the various microservices.**


![[e-comerce .png]]

- 1. User apps - the point where the user interacts with the application
- 2. API Gateway - this acts as a single point entry for all client requests and routes them to the appropriate microservice
- 3. Microservices - each part will handle its own specific section of the required app. as the e-commerce example above, 1 is for products, 1 is for cart/checkout and 1 is for orders
- 4. Database - Each microservice will have its own database holding the relevant information for that particular microservice

## Importance

- Scalability - again, each section can be scaled without effecting the others, useful when the app could have thousands of microservices working independently of each others
- Flexibility - the use of microservices allows developing teams to use different tech and programming languages that would best suit the need without conflicts with the other microservices
- Resilience - If one microservice should go down or have an issue it wont affect the others, so this makes the web app even more reliable

Microservices Architecture is the most common form due to its flexibility and maintainability.

---
# References
