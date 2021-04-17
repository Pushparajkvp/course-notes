# Thinking process while designing a system

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
