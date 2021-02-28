# Basics

## Load Balancers

1. What?
   1. It helps to distribute load across multiple resources
   2. It also keeps track of status of all the reource(health) to avoid routing requests to nodes that are down or low performant
2. Where?
   1. User - Web server
   2. Web server - Internal servers (reverse proxy)
   3. Internal server - databse
3. Types
   1. Hardware load balancers
   2. Software laod balancers (HAProxy)
4. Algorithms
   1. Roud Robin
   2. Round Robin with weighted server
   3. Least connections
   4. Least response time
   5. source IP hash
   6. URL hash

## Chaching

1. What?
   1. It is a short term memory which has limited space and provides faster access
2. Where?
   1. Hardware (RAM)
   2. OS
   3. Web browsers
   4. Web applications
   5. everywhere
3. Types
   1. Application server cache (cache in app server)
   2. Distributed cache (cache which is based on consisted hashing)
   3. Global cache (central cache)
   4. CDN (to serve static contents)
4. Cache Invalidation
   1. When data is modified in DB, it should be invalidated in cache
   2. Types
      1. Write-through -> write both on cache and db
      2. Write around -> write in db and clear cache
      3. Write back -> write to cache alone and persist later
5. Cache Eviction policies
   1. FIFO
   2. LIFO
   3. LRU
   4. Most recently Used
   5. Least Frequently Used
   6. Random replacement

## Sharding

1. What?
   1. Breaking the big database into multiple smaller shards
   2. It helps in horizontal scaling
   3. It also helps in replicating data/backup
2. Methods
   1. Horizontal Partitioning
      1. Putting different rows in different DB
      2. Range based sharding
   2. Vertical Partitioning
      1. Divide tables based on features (Micro services)
   3. Directory based paritioning
      1. Directory based shard partitioning involves placing a lookup service in front of the sharded databases.
3. Criteria
   1. Hash based
   2. List partitioning
   3. Round robin
   4. Composite -> combination of above
4. Challenges
   1. ACID compliance
   2. Join Inefficeincy

## Indexing

1. What?
   1. It is a data structure that we apply over existing table
   2. Used to improve the speed of queries
   3. Index makes trade-off of increasing speed of read by giving up some storage and write speed
   4. Index is a data structure of table of contents that points us to the location where actual data lives
   5. We store that column and the pointer to the whole row as index
2. Types
   1. Ordered indexing (ASC or DSC ordering)
   2. Hash indexing (Hash function of rows)
   3. btree

## Proxy

1. What?
   1. A server that sits between client and server
2. Why?
   1. To coordinate request to multiple server (reverse proxy)
   2. Filtering
   3. ACL
   4. Adding / removing headers
   5. Caching

## Messaging Queues

1. What?
   1. Asynchronous service-to-service communication used in serverless and microservice architectures
   2. Used to send data between services
2. How?
   1. Producer -> one who produces the data
   2. Consume -> one who consumes the data
   3. Messages are stored in queue by producer until they are processed by consumer and deleted
3. Examples
   1. Kafka
   2. RabbitMQ

## SQL / NoSQl

1. What SQL?
   1. Stored in row/column
   2. Fixed schema -> columns must be decided before adding or reading data
   3. It used SQL queries
   4. SQL are vertically scalable
   5. It supports ACID property
2. What NoSQL?
   1. Schema is dynamic
   2. Queries are focused on a collection of documents. It's called UNQL (Unstructured Query Language)
   3. Columns can be added on the fly and each row need not have all the columns
   4. These are horizontally scalable
   5. They don't support ACID property
   6. Good for cloud based computing/storage
3. Types NoSQL
   1. Key-Value stores -> Redis
   2. Document Based -> mongo db
   3. Wide-Column database(Column families)
      1. Data is stored in number of columns
      2. Cassendra
   4. Graph Databse
      1. Data is stored as nodes, properties and lines
      2. InfiniteGraph
4. When to choose SQL?
   1. Schema is not going to change
   2. When we need ACID properties
5. When to choose NoSQL?
   1. When schema is dynamic
   2. When storing large data with no structure
   3. When data needs to be stored accross regions and many server

## Monolithic / Microservices

1. What Monolithic?
   1. It's a big application which has all it's components tightly coupled
   2. Issues
      1. New features are hard to implement
      2. Hard to scale
      3. Whole system can go down easily
      4. Single framework
2. What Microservice?
   1. Decomposed version of monolithic architecture
   2. Different services use different components and communicate with each other
   3. Each server has LB, Index, REST api
   4. Benefits
      1. Does one thing very well
      2. Standalone
      3. Decoupled
      4. Continuous delivery
      5. Autonomy
      6. Scalable
3. Best practicies
   1. Separate data store
   2. Separate as per feature
   3. Server which is stateless

## REST APIs

1. What?
   1. A service is RESTful if it follows,
      1. Uniform interface
         1. service is resource based
         2. Manipulation is allowed through representation
         3. Message is self descriptive
      2. Stateless
         1. No need to store the state
      3. Cachable
      4. Client Server code must be seperate
1. Methods
   1. GET
      1. This request is used to get a resource from a server
      2. In other words, a GET request performs a READ operation
   2. POST
      1. This request is used to create a new resource on a server
      2. In other words, a POST request performs an CREATE operation.
   3. PUT/PATCH
      1. These two requests are used to update a resource on a server.
      2. In other words, a PUT or PATCH request performs an UPDATE operation.
   4. DELETE
      1. This request is used to delete a resource from a server.
      2. In other words, a DELETE request performs a DELETE operation

## Consistent Hashing

1. What?
   1. Consistent Hashing is a distributed hashing scheme that operates independently of the number of servers or objects in a distributed hash table by assigning them a position on an abstract circle, or hash ring
   2. This allows servers and objects to scale without affecting the overall system.
   3. Suppose our hash function output range in between zero to 2**32 or INT_MAX, then this range is mapped onto the hash ring so that values are wrapped around
   4. In consistent hashing we need to map only k/n again where k is number of keys and n is server.
   5. Generally if we have 'K mod n' way of hashing, adding a new server will need rehashing every thing.

## Kafka

1. What?
   1. It is Async amessage queue
   2. Distributed streaming platform that is used for publish and subscribe to streams of records
2. How?
   1. IT used IO efficiently by batching and compressing records
   2. It is used for decoupling data streams
   3. It retains all published records unless a limit is set
   4. It is a scalable message storage
3. Components
   1. Producer
   2. Consumer
   3. Broker -> Producer and consume interact through kafka broker server
   4. Cluster -> Distributed cluster of servers
   5. Topic -> Identification of a stream
   6. Partition -> Break kafka topics to multiple partitions
   7. Offet -> Sequence ID given to message as they arrive at partition
   8. Topic name + Partition number + offset -> locats the exact message
   9. Consumer group -> Group of consumers who share the same

## Hadoop

1. What?
   1. Collection of open source software that facilitate using network of many computers to solve problems involving massive amount of data
   2. It provides a software framework for distributed storage and processing of big data using map reduce
   3. Fault and hardware failure tolerant
2. How?
   1. Core of hadoop consists of a 2 parts,
      1. storage part known has Hadoop Distributed File System(HDFS)
      2. Processing part MapReduce
   2. It splits files into large blocks and distributes them across nodes in a cluster.
   3. It then sends packaged code into the nodes to process the data in parallel
3. Components
   1. Hadoop common -> libraries and utilities needed
   2. HDFS -> distributed file system
   3. Hadoop yarn -> responsible for managing computing resources
   4. Hadoop MapReduce -> MapReduce programming model for large-scale data processing

## Zookeeper

1. What?
   1. It coordinates between distributed applications
2. Features
   1. It maintains configuration information across all nodes
   2. Providing names to nodes
   3. It provides distributed snychronization: locals,barriers, queues
   4. Provides leader selection
      1. All nodes have info about each other so if leader dies another can be elected
   5. Replication
   6. Consistency

## Desinging a system

1. Requirements
2. API Creation
3. Database design
4. Logic to solve problem
5. System workflow
6. Load Balance
7. Chaching
8. Sharding
9. Indexes
10. Message Queues
11. Hashing
12. LRU
13. Hadoop
14. cassandra
15. Microservices
