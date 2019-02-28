# Apache-Kafka

## Useful Resources
1. [Official documentation](https://kafka.apache.org/)

## Overview of Kafka: a Distributed Streaming Platform
1. Three key capabilities:
    1. **Publish and subscribe** to streams of records, like a message queue or enterprise messaging system
    2. Store streams of records in a **fault-tolerant durable way**.
    3. Process streams of records in **real-time**.
2. Basic concepts of Kafka:
    1. Kafka runs as a cluster on one or more servers that can span multiple datacenters.
    2. Kafka cluster stores streams of records in categories called topics.
    3. Each reoord consists of a key, a value, and a timestamp.
3. Four Core APIs:
    1. Producer API: allows an application to publish streams of records to one or more topics
    2. Consumer API: allows an application to subscribe one or more topics and process streams of records that produced to them.
    3. Streams API: allows an application to act as a stream processor that effectively transforms the input streams to output streams.
    4. Connector API: manages integration of Kafka connect with other systems. It has two main tasks:
        1. Given some configuration, they are responsible for creating configurations for a set of Tasks that split up the data processing.
        2. They are responsible for monitoring inputs for changes that require reconfiguration and notifying the Kafka Connect runtime via the ConnectorContext.
4. Kafka is generally used for two broad classes of applications:
    1. Building **real-time streaming data pipelines** that reliably get data between applications or systems. 
    2. Building **real-time streaming applications** that transform or react streams of data.

5. Kafka as a Messaging System VS Traditional Enterprise Messaging System
    1. Traditional Messaging System has two models: **Queuing** and **Publish-Subscribe**
        1. Queuing: a pool of consumers read from a server and each record goes to one of them.
            1. Advantages: **scalability**, allows dividing up the processing of data over multiple consumer instances
            2. Disadvantages: 
                1. **No multi-subscriber**: once one process reads the data, it's gone.
                2. **No parallelism in processing**: although the server hands out records in order, the records are delivered asynchronously to consumers and they may arrive out of order on different consumers. Therefore, messaging systems may allow only one process to consume from a queue and there is no parallelism in processing.
        2. Publish-Subscribe: the record is broadcast to all consumers.
            1. Advantages: multi-subscriber, allows broadcast data to multiple processes. 
            2. Disadvantages: no scalability, every message goes to every subscriber.
    2. Kafka as a messaging system: a combination of queuing and publish-subscribe
        1. Kafka can scale processing
        2. Kafka allows multi-subscriber
        3. Ordering guarantees: by having partition within the topics, Kafka is able to to provide both ordering guarantees and loading balancing over a pool of consumer processes. Each partition is consumed by exactly one consumer in the group and there cannot be more consumer instances in a consumer group than partitions.



