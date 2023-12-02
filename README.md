# Educational Example (Work in Progress)

## Technologies Used
- SpringBoot
- Spring Security
- Maven
- Spring Cloud Gateway
- ~~Netflix Zuul~~ (no longer supported by Spring)
- Eureka (Discovery Service)
- Ribbon
- Spring Cloud Stream
- Apache Kafka (Message Broker)
- Zookeeper (manages and controls brokers in Apache Kafka cluster)
- JWT (Token Authenticator)
- Docker
- FeignClient
- Hystrix
- Lombok
- Hibernate
- Neo4j
- Cassandra

## Application Description
- **ApiGateway**: Gateway to the Front-End (FE)
- **AuthService**: Manages authentication and creation of new users
- **PostService**: Creates posts
- **FeedService**: Retrieves user's feed
- **DiscoveryService**: Service directory
- **GraphService**: Stores relationships between users

## Future Enhancements
- Front-End in React
- Scale the application using Kubernetes

## Understanding Zuul and Eureka
We have an API gateway which receives requests from the FE. Zuul handles these requests. When a request requires Service A, Eureka provides all instances of Service A and supplies them to Ribbon. Ribbon then chooses which instance to use for load balancing.

## Apache Kafka
Apache Kafka is used for internal communication between services. It follows the publish-subscribe model. It consists of producers that send messages to topics and partitions within a cluster. This cluster contains brokers managed by Zookeeper. Consumers then sequentially retrieve messages intended for them, keeping track of their OFFSET to know which message to consume next.

### Key Components of Kafka
- Publish-subscribe messaging system
- Topics (Categories for messages)
- Messages in topics have four attributes: key, value (both mandatory), and optional timestamp and headers
  - The value can be anything
- Main components of Kafka:
  - **Broker**: Handles all requests from clients (produce, consume, and metadata) and maintains data replication within the cluster. A cluster can have one or more brokers.
  - **Zookeeper**: Maintains the state of the cluster (brokers, topics, users).
  - **Producer**: Sends records to a broker.
  - **Consumer**: Consumes batches of records from the broker.
