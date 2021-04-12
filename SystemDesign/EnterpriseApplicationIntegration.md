# Enterprise application integration

1. Enterprise application integration (EAI) is the use of software and computer systems' architectural principles to integrate a set of enterprise computer applications.

## Overview

1. EAI is an integration framework composed of a collection of technologies and services which form a middleware
2. Information Silos or island of automation
   1. Business softwares like supply chain management applications, ERP systems, CRM applications for managing customers, business intelligence applications, payroll, and human resources systems typically cannot communicate with one another in order to share data or business rules.
   2. such applications are sometimes referred to as islands of automation or information silos.
   3. Disadvantages
      1. identical data are stored in multiple locations
      2. straightforward processes are unable to be automated.
      3. Additional manual work
3. EAI is the process of linking such applications within a single organization together in order to simplify and automate business processes to the greatest extent possible, while at the same time avoiding having to make sweeping changes to the existing applications or data structures
4. How?
   1. back-end api
   2. rarely GUI
5. Systems have different
   1. OS
   2. DB
   3. Language
   4. date time formats

## Purpose

1. Data Integration also known as Enterprise Information Integration(EII)
2. Vendor independence
3. Common facade : An EAI system can front-end a cluster of applications, providing a single consistent access interface to these applications and shielding users from having to learn to use different software packages.

## Patterns

1. Integration pattern
   1. Mediation (intra-communication)
      1. Here, the EAI system acts as the go-between or broker between multiple applications.
      2. Whenever an interesting event occurs in an application (for instance, new information is created or a new transaction completed) an integration module in the EAI system is notified.
      3. The module then propagates the changes to other relevant applications.
   2. Federation (inter-communication)
      1. All event calls from the 'outside world' to any of the applications are front-ended by the EAI system.
      2. The EAI system is configured to expose only the relevant information and interfaces of the underlying applications to the outside world
   3. Both patterns are often used concurrently.
2. Access pattern
   1. asynchronous
      1. used in mediation pattern more
   2. synchronous
      1. used in federation pattern more
3. Lifetime patterns
   1. short-lived
      1. e.g., keeping data in sync across two applications could be completed within a second
   2. Long-lived
      1. e.g., one of the steps could involve the EAI system interacting with a human work flow application for approval of a loan that takes hours or days to complete

## Topologies

1. Spoke–hub distribution paradigm
   1. the EAI system is at the center (the hub)
   2. interacts with the applications via the spokes.
2. Bus model
   1. EAI system is the bus
   2. Is implemented as a resident module in an already existing message bus or message-oriented middleware

## Technologies

1. Bus/hub
   1. This is usually implemented by enhancing standard middleware products (application server, message bus) or implemented as a stand-alone program that act as middleware.
2. Application connectivity
   1. The bus/hub connects to applications through a set of adapters (also referred to as connectors).
   2. These are programs that know how to interact with an underlying business application.
   3. The adapter performs one-way communication(unidirectional), performing requests from the hub against the application
   4. notifying the hub when an event of interest occurs in the application
3. Data format and transformation
   1. To avoid every adapter having to convert data to/from every other applications' formats, EAI systems usually stipulate an application-independent (or common) data format.
   2. The EAI system usually provides a data transformation service as well to help convert between application-specific and common formats.
   3. two steps
      1. The adapter converts information from the application's format to the bus's common format.
      2. semantic transformations are applied on this (converting zip codes to city names, splitting/merging objects from one application into objects in the other applications, and so on).
4. Integration modules
   1. Integration modules subscribe to events of specific types and process notifications that they receive when these events occur.
5. Support for transactions
   1. When used for process integration, the EAI system also provides transactional consistency across applications by executing all integration operations across all applications in a single overarching distributed transaction (using two-phase commit protocols or compensating transactions).
