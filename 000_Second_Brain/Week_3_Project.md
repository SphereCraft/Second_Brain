04/09/2024 0625

Status #idea

Tags:

# Week 3 Project

# 🚀 Project - Create your Architecture

##### [Week 3 - System Design Applications](https://cloudengineeracademy.mykajabi.com/products/cloud-academy-tech-with-soleyman/categories/2154687876)

### Designing and Comparing Architectural Styles

#### Objective:

You will design a simple e-commerce application using monolithic architecture, then refactor it into microservices, and finally, propose a server-less approach for certain functionalities. This exercise aims to provide practical insights into the advantages, challenges, and use cases of each architectural style.

#### Part 1: Monolithic Architecture Design

1. **Design a Simple E-commerce Application:**
    - Define the core functionalities: user registration, product catalogue, shopping cart, and order processing.
    - Create a high-level architecture diagram showing the UI, business logic/back-end, and data interface layers.
    - Discuss the simplicity and uniformity advantages and address the scalability, flexibility, and deployment disadvantages within the context of your design.

#### Part 2: Refactoring into Microservices

1. **Identify and Design Microservices:**
    - Break down the monolithic design into microservices (e.g., User Service, Product Service, Cart Service, Order Service).
    - Draw an updated architecture diagram showing the microservices, their databases, and how they interact with the UI and each other.
    - Explain how this refactoring addresses the scalability and flexibility issues. Discuss the challenges in deployment, development, and maintaining consistency.

#### Part 3: Incorporating Serverless Architecture

1. **Serverless Functions for E-commerce:**
    - Identify components of the microservices design that could be effectively handled by serverless functions (e.g., user authentication, payment processing).
    - Update the architecture diagram to include serverless functions and their triggers.
    - Discuss the benefits of serverless architecture in terms of scaling, cost, and operational management. Highlight the differences and potential challenges compared to microservices.

#### Deliverables:

- **Architecture Diagrams:** For each part of the exercise, provide a detailed architecture diagram illustrating the design.
- **Comparison Report:**
    - Write a report comparing the three architectural styles, focusing on scalability, development complexity, deployment, maintenance, and cost implications.
    - Include a section on the suitability of each architecture style for different types of projects (e.g., small vs. large scale, consistent load vs. variable load).


**Part 1**
Main functions of the e-commerce design are as stated, user registration, product catalogue, shopping cart, and order processing. In a basic diagram the structure could look something like this
![[Ecommerce basic design (mono).png]]

This style of architecture is good for smaller systems without much scope to scale. If a larger company is looking to expand their store then my suggestion would be to look at different ways to achieve this. 
Scalability options here are limited due to the basic and compact nature of this design. Each core area would need to be scaled all together, this in turn can be great for smaller companies with smaller team, but will become more complex as things grow. Needing to update the whole app instead of the sections that required changes is another disadvantage.
But overall its a nice compact, simple to use and simple to maintain design.
In my diagram above i kinda skipped a stage and implemented the micro services ahead of time, that is part 2

**Part 2**
![[Ecommerce basic design (mono).png]]

By adding in the micro services this can help with the flexibility and scaling issues. Each section (Registration, catalogue, cart and processing) can now be maintained, updated and scaled individually, helping to manage the system more efficiently. But due to the monolithic nature of the design there are still limits within the design.

![[serverless structure.png]]

Although this seems the same, the micro services are now controlled, fully automated by [[Lambda Function]] allowing for greater flexibility and scalability. Giving this control to [[Lambda Function]] will give it the control to maintain and scale as and when needed. This has quite an impact on costs, ie only pay for what is being used and any given time.
Things could be changed and make as much of the process as possible fully automated using a full server-less design 

![[Ecommerces erverless.png]]

This will allow for even greater scaling and flexibility will the managing done automatically

# 🚀 Project - Design Scalable Architecture

##### [Week 3 - System Design Applications](https://cloudengineeracademy.mykajabi.com/products/cloud-academy-tech-with-soleyman/categories/2154687876)

For this project, you will design an architecture for a scalable web application. You will create two versions of the design: one using traditional server scaling (both vertical and horizontal) and another leveraging serverless technologies. This exercise aims to illustrate the practical applications of load balancing, API gateways, and different scaling strategies in real-world scenarios.

#### Part 1: Traditional Server Scaling Design

1. **Design Overview:**
    
    - Propose a web application idea (e.g., e-commerce platform, social media site) and outline its core functionalities.
    - Create a high-level architecture diagram incorporating load balancers, web servers, application servers, and databases.
2. **Vertical and Horizontal Scaling:**
    
    - Explain how you would implement vertical scaling for your database layer.
    - Design a horizontal scaling strategy using an Auto Scaling Group for the web and application server layers. Include a load balancer in your architecture to distribute incoming traffic.
    - Discuss the benefits and limitations of each scaling strategy in the context of your application.

#### Part 2: Serverless Architecture Design

1. **Serverless Components:**
    
    - Redesign the architecture of the same web application using AWS Lambda functions for backend processing.
    - Incorporate other serverless services (e.g., Amazon DynamoDB, API Gateway) to support your application's functionalities.
    - Include a diagram showing how these serverless components interact with each other and how they're exposed to the front end.
2. **Scaling and Management:**
    
    - Discuss how serverless architecture simplifies scaling and management aspects of the application.
    - Highlight the differences in scaling behavior between serverless and traditional server-based scaling, emphasizing aspects like cost, operational overhead, and scalability limits.

#### Part 3: Comparison and Analysis

1. **Performance and Cost:**
    
    - Compare the two architectures in terms of performance under varying load conditions and cost-efficiency at scale.
    - Consider the implications of each architecture on development, deployment, and maintenance.
2. **Use Cases:**
    
    - Identify scenarios where one architecture might be preferred over the other, considering factors like application complexity, traffic patterns, and operational capacity.


In answer to the project above, i feel that I've covered it all ahead of time in the previous project with a basic e-commerce design scaling from the traditional version to the cloud based system. Horizontal and vertical scaling will depend on the service requested. this traditional method would be best suited for smaller or legacy applications due to the limiting factors with scaling.
Moving on to the cloud based system, this will allow all the services to be scaled on demand, as and when its needed. Thus reducing any downtime, maintenance to keep the user happy unknowing what is actually going on.
I understand this isn't really the full write up but i will be understanding more as i go and will re visit later on and sure will be doing more in depth project and getting more aware and better at this process.

# References
