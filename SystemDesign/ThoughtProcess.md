# Thinking process while designing a system

## Steps

1. Requirements clarifications
   1. Clarify Ambiguity
   2. Define end goals clearly
   3. Decide which part of the system to focus on
   4. Twitter like system example
      1. Will users of our service be able to post tweets and follow other people?
      2. Should we also design to create and display the user’s timeline?
      3. Will tweets contain photos and videos?
      4. Are we focusing on the backend only, or are we developing the front-end too?
      5. Will users be able to search tweets?
      6. Do we need to display hot trending topics?
      7. Will there be any push notification for new (or important) tweets?
2. Back-of-the-envelope estimation
   1. What scale is expected from the system
   2. How much storage will we need?
   3. What network bandwidth usage are we expecting?
3. System interface definition
   1. Define APIs
   2. Ensure the APIs fullfill the requirements
4. Defining data model
   1. Identify entities in the system
   2. How they interact
   3. Various aspects of data
   4. RDBMS or NoSQL?
5. High-level design
   1. representing the core components of our system
   2. Use physical components that are critical without worrying about scale and performance
6. Detailed design
   1. Start the components deeper
   2. Discuss about various approaches and trade-offs
   3. decide on which is better for current system
7. Look for bottlenecks
   1. Identify Single Point of Failures
   2. High Load scenarios
   3. Monitoring performance of the services

## Choosing Database

1. Nature of data
   1. RDBMS
      1. easily be expressed in tabular form choose RDBMS
   2. NoSQL
      1. complex and has multi level nesting choose NoSQL
      2. volatile schema choose NoSQL
      3. If only read and write is needed with eventual consistency NoSQL can be preferred
      4. Types of NoSQL to prefer
         1. Semi-structured JSON like data -> Document database -> mongoDB
         2. Relationship heavy system -> Graph DB -> Neo4J
         3. Fast access data -> key value pair O(1) -> Redis, Memcahe
         4. Time Series Data -> Time Series Database -> Prometheus, Influx
         5. Big data -> Column wide database -> cassandra
2. CAP tradeoff
   1. RDBMS
      1. When ACID(Atomicity Consistency Isolation Durability) is a must
      2. When Data schema won't change rapidly
   2. NoSQL
      1. When BASE(BAsically Available, Scalable and Eventually Consistent) is needed
      2. When Data schema will change rapidly
      3. When it is simple read and write withou complex reltionships

## System Integration

1. Gather functional and non functional requirements
2. How immediate should the information be intergrated
3. Check the reliability and availability of the integration systems
4. Check if it is request/response or event driven
5. Identify if sync or async communication is required
   1. If sync
      1. Check the reliability of the responder
      2. Availability of the responder
      3. If responder is not really available then
         1. have a fallback to another component
         2. Do circuit breaking
         3. Try to cache and use during downtime
      4. If the responder is not reliable
         1. Do data transfoormation
         2. data validation
   2. If async
      1. Find the producers of event
      2. Find the consumers of event
      3. Relationship between producers and consumers
      4. Check if multiple consumers can consume a event or just one
6. Estimate the amount of data
7. Decide on sync delay