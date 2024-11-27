202407271511

Status #idea

Tags:

# Monolithic Architecture

It is a single tiered software application pattern built as a single and indivisible unit. This typically contains 3 main components

- User Interface
- Business Logic/Back-end
- Data Interface

The user interface is the front end part of the system where users interact with the software, its responsible for collecting user input and displaying data from the system

The Business Logic contains the core computational of the application. It takes the user inputs and processes it using the business rules and makes decisions based on the user inputs.

The data interface AKA Data Access Layer
This part is responsible for talking with the database.It handles the retrieval, updates date and stores data based on the actions preformed but the business logic section.

All 3 components are tightly integrated and run as a single service. So if you need to upgrade or update, you typically have to do this to the whole stack. Even if the part you wish to update is small you have to deploy all 3 components.
Mono is the key word, it all works together, if need applications that works independently find something else.

How does it work?

It works in the order 
- User makes an input
- that gets sent to the back end (business logic)
- Depending what has been asked from the application, the data interface may access the database
- then the response gets returned to the user

Pros and cons
	Pros
	- Simplicity, for smaller businesses and smaller team it could be advantages to use monolithic architecture as its designed in one simple code base
	- very simple to interact
	- simple to use
	- simple to maintain for small teams
	-this can make it simple to debug and maintain
	Cons
	- Can be more complex to scale as will need to scale the whole application instead of just the parts that need scaling
	- Flexibility, can be awkward to make changes on one part and it can effect the rest of the system
	- Deploying new versions of the application can take longer due to all the parts needing to be deployed.


So why do we care?

Legacy systems are generally monolithic. This could change with time, but existing systems are usually mono.
Knowing about monolithic systems can help us to understand the best way to approach integrations with other systems in the cloud.
As cloud experts we need to understand how to scale mono correctly, using horizontal scaling as an example
monolithic application tend to use resources differently, so need to understand to resolve problems more efficiently.
Cost, have to know what the application uses, so we can select the right resources to be a s cost effective as possible.

Manly used for smaller

---
# References
