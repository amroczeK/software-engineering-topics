# Software Architectural Patterns
Software architectural patterns are a general, reusable solution to a commonly occurring problem in software architecture within a given context. These patterns serve as templates that guide software developers in designing software architectures.

Here are some of the most popular architectural patterns:

### **Monolithic Architecture:** 
This architecture designs the application as a single and indivisible unit. Changes to any component require rebuilding and deploying the entire application. Monolithic architectures are easy to develop, test, and deploy. However, as they grow, they become harder to understand, modify, and scale.

### **Layered (n-tier) Architecture:** 
This pattern breaks up the application into grouped functionality known as layers, such as presentation, business, and data access layers. Each layer has specific roles and responsibilities and is designed to be independent of the others.

### **Microservices Architecture:** 
This architectural style structures an application as a collection of loosely coupled services, which implement business capabilities. Microservices can be developed, deployed, and scaled independently. They allow organizations to create CI/CD pipelines for each service independently.

### **Event-Driven Architecture:** 
In this architecture, events (changes in state) are detected by event listeners and processed by appropriate event handlers. This can be a simple publish/subscribe system or can involve complex event processing.

### **Service-Oriented Architecture (SOA):** 
SOA designs the application as a collection of services that communicate with each other through simple data passing or activity coordination. Each service is independently deployable, but they operate together to fulfill a business goal.

### **Domain-Driven Design (DDD):** 
DDD is more of a methodology than an architectural pattern. It focuses on core domain logic, complex designs, and collaborations between domain-driven designs and other architectural patterns.

### **Model-View-Controller (MVC):** 
This architectural pattern separates an application into three interconnected components: the model, the view, and the controller. It's a popular pattern for designing web applications.

### **Model-View-ViewModel (MVVM):** 
This pattern is widely used in Microsoft's WPF, Silverlight, and more recently in JavaScript frameworks like Angular and Vue.js. It separates responsibilities into Model (data), View (UI), and ViewModel (an abstraction of the View exposing public properties and commands).

### **Serverless Architecture (Function as a Service or FaaS):** 
This architecture removes the need for the traditional 'always on' server system sitting behind an application. Instead, developers can execute their code in response to events or HTTP requests.

### **Container-based Architecture:** 
This architecture involves packaging and distributing software in containers, which include all the libraries, dependencies, and other necessary parts to run. Containers allow for better scalability and resource usage compared to traditional VMs. Docker and Kubernetes are popular tools in this space.

These architectural patterns are not exclusive, and you may often find them used in combination in real-world applications. The choice of architectural pattern depends on the specific needs and constraints of your project.

## Example Use cases

### **Monolithic Architecture:** 
An online shopping website where all the features like user management, product catalog, cart management, payment processing, etc., are handled in a single application. This is easy to manage and deploy initially, but can become complex and difficult to scale as the application grows.

This architecture is common in small to medium-sized applications where all the functionality resides in a single application. An example might be a small web application like a blog or a single-user system where all components (database, client-side, server-side) are interconnected and run as a single service.

### **Layered (n-tier) Architecture:** 
An enterprise web application with separate layers for presentation, business logic, and data access. The user interface (presentation layer) interacts with the business logic layer, which in turn interacts with the data access layer.

Any enterprise application that separates its layers, for instance, a typical e-commerce website like Amazon. It has separate layers for the frontend (UI), business logic (add to cart, calculate discounts), and data access (interaction with databases or services to retrieve product details).

### **Microservices Architecture:** 
A food delivery app like UberEats or DoorDash where different functionalities (user service, restaurant service, order service, delivery service, etc.) are divided into microservices. Each microservice can be developed, deployed, and scaled independently.

Companies like Netflix, Amazon, and Uber use microservices. For instance, Netflix has different microservices for recommendations, movie lists, account services, etc. Each of these can be developed, deployed, and scaled independently.

### **Event-Driven Architecture:** 
A stock market application where changes in stock prices generate events, which then trigger additional processes like notifications to interested subscribers.

Event-driven architecture is commonly used in real-time analytics and for asynchronous workflows. A real-world example could be a notification system: when a user performs an action (like making a purchase), it triggers an event to send a notification.

### **Service-Oriented Architecture (SOA):** 
An airline reservation system where different functionalities (reservation, payment, notification, etc.) are exposed as services. These services can communicate with each other to accomplish a business goal.

An example could be a weather information system that pulls data from multiple sources (each source being a separate service), processes it, and serves the processed information to clients.

### **Domain-Driven Design (DDD):** 
A banking system where complex domain rules exist. Different subdomains like accounts, loans, and credits are separated into bounded contexts and implemented using the principles of DDD.

Any complex system with multiple domains can benefit from DDD. As an example, a large e-commerce platform can have separate domains for inventory, billing, shipping, etc., each with its own complex logic.

### **Model-View-Controller (MVC):** 
An online forum system where the Model represents the data and the business rules, the View represents the user interface, and the Controller manages the communication between the Model and the View.

This pattern is commonly used in web application frameworks. For example, Ruby on Rails and ASP.NET MVC frameworks follow the MVC pattern.

### **Model-View-ViewModel (MVVM):** 
This pattern is popular in desktop application development. For instance, it's commonly used in WPF and Silverlight applications for Windows, and by frameworks like Angular in the web development world.

### **Serverless Architecture (Function as a Service or FaaS):** 
AWS Lambda functions are a good example of this. You can write code for tasks like image processing or automated backups, and then run that code in response to events or on a schedule, without having to manage a server yourself.

### **Container-based Architecture:**
Google Cloud Platform and Amazon Web Services (AWS) make extensive use of containerization. For instance, you might have a complex application where each microservice runs in its own container, and you use Kubernetes to manage those containers.