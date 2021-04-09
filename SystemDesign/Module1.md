# Module 1

## Overview

Go step by step through the different components and concepts involved in architecting a web application.

## Module Objectives

1. Understand the concepts, components, and technology trade-offs involved in architecting a web application.
2. Learn various architectural styles such as the client-server, peer to peer decentralized architecture, the fundamentals of data flow in a web application, concepts like scalability, high availability and much more.
3. Master the techniques of picking the right architecture and the technology stack to implement a use case.

## Different Tiers in Software Architecture

1. Introduction
   1. Think of a tier as a logical separation of components in an application or a service.
   2. physical separation at the component level
   3. components
      1. Database
      2. Backend application server
      3. User interface
      4. Messaging
      5. Caching
2. Single Tier Applications
   1. A single-tier application is an application where the user interface, backend business logic & the database all reside in the same machine.
   2. Advantages
      1. no network latency
      2. data is easily & quickly available
      3. data of the user stays in his machine
   3. Disadvantages
      1. Business has no control over the application
      2. no code or features changes can possibly be done until the customer manually updates
      3. vulnerable to being tweaked & reversed engineered
3. Two Tier Application
   1. A Two-tier application involves a client and a server. The client would contain the user interface & the business logic in one machine. And the backend server would be the database running on a different machine. The database server is hosted by the business & has control over it.
   2. Need for 2 tier
      1. to-do list app or a similar planner or a productivity app
      2. fewer network calls
      3. online browser & app-based games
         1. get downloaded on the client just once
         2. network calls only to keep the game state persistent.
4. Three Tier Applications
   1. In a three-tier application, the user interface, application logic & the database all lie on different machines & thus have different tiers. They are physically separated.
5. N tier applications
   1. An N-tier application is an application which has more than three components involved.
   2. components
      1. Cache
      2. Message queues for asynchronous behaviour
      3. Load balancers
      4. Search servers for searching through massive amounts of data
      5. Components involved in processing massive amounts of data
      6. Components running heterogeneous tech commonly known as web services etc.
   3. There is another name for n-tier apps, the “distributed applications”
   4. Need for N-tier
      1. Two software design principles that are key to explaining this are the Single Responsibility Principle & the Separation of Concerns.
      2. Single Responsibility Principle
         1. Single Responsibility Principle simply means giving one, just one responsibility to a component & letting it execute it with perfection
         2. This approach gives us a lot of flexibility & makes management easier.
         3. Dedicated teams & code repositories for every component
         4. Single responsibility principle is a reason why I was never a fan of stored procedures.
         5. Stored procedures enable us to add business logic to the database
         6. A database should not hold business logic, it should only take care of persisting the data
      3. Separation Of Concerns
         1. Separation of concerns kind of means the same thing, be concerned about your work only & stop worrying about the rest of the stuff.
         2. Keeping the components separate makes them reusable. 
         3. Different services can use the same database, the messaging server or any component as long as they are not tightly coupled with each other.
      4. Having loosely coupled components is the way to go. The approach makes scaling the service easy in future when things grow beyond a certain level.
   5. Difference Between Layers & Tiers
      1. The difference between layers and tiers is that the layers represent the organization of the code and breaking it into components.
      2. Tiers involve physical separation of components
