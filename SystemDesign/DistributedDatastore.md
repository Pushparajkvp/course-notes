# Distributed Data Store (Cassandra)

1. Intro
   1. Distributed datastore like cassandra and various NoSQL databases have eventual consistency
   2. They offer horizontal scalability and efficient read and write
   3. They have a cluster of nodes serving request
2. Node responsiblity in cluster
   1. They serve request
   2. They have backup of another node
3. Data partitioning
   1. The logic of storing part of data in different machines is called partitioning
4. Consisten hashing
   1. Data is stored in nodes in ring format
   2. Every NoSQL database had a partition key to store data
   3. Partition key is hashed and the resultant value is stored in node resposible
5. Replication  
   1. The data is replicated across nodes for fault tolerance based on replication factor
   2. The replication can be sequential or other stratergy
6. Rebalancing (Gossip)
   1. When I want to add new node in the cluster rebalancing happens
   2. The responsibility range is changed and shared with the nodes
   3. They gossip to understand state of each node
   4. The data is transferred to the new node
7. Node failure
   1. Gossip is not heard from the node
   2. Responsibility is shifted to the new Node
   3. New node gets data from redundant places and serves request
