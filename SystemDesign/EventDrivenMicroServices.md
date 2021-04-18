# Event Driven Microservices using Kafka

## Intro

1. History
   1. Traditional Approach (Sync request response)
   2. ![Traditional](images/EDNTraditional.jpg)
   3. SOA architecture
   4. ![SOA](images/EDNTraditional.jpg)
   5. Virtualized SOA
   6. ![Virtualized SOA](images/VirtualisezSoa.jpg)
   7. Microservices
      1. Microservices (Decoupling of SOA) -> Sync
      2. ![Microservices](images/Microservices.jpg)
      3. Microservice (api gateway/ virtualized SOA) -> Sync
      4. ![Microservices Sync](images/MicroserviceAPIGateway.jpg)
      5. Sync problem with failure
      6. ![Microservices failure](images/MicroserviceFailure.jpg)
2. Event-Driven
   1. Sync at front end and inter process communication is event based
   2. ![Micro Async](images/MicroservicesAsync.jpg)
   3. Streaming analytics
   4. ![Micro stream Async](images/MicroservicesStreamAsync.jpg)
   5. Legacy system integration
   6. ![Micro Legacy Sysytem](images/MicroLegacysystem.jpg)
3. Pub/Sub
   1. Messaging pattern
      1. Senbder publishes message without knowing about receivers
      2. Receiver subscribes to the topic without knowing if there are any senders
   2. They have a broker to decouple
4. Distributed Event log
   1. Messages are persisted on disk
   2. Retention Policy
