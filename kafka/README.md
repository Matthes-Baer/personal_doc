# Apache Kafka

## Useful Links

- [Kafka Crash Course](https://www.youtube.com/watch?v=B7CwU_tNYIE)

## General Information

- Kafka is a **distributed streaming platform** for:
  - Messaging (pub/sub)
  - Event streaming
  - Log aggregation
  - Real-time analytics
- Key concepts:
  - **Broker**: Kafka server that stores and serves messages
  - **Topic**: Named category for messages
  - **Partition**: A topic is split into partitions for scalability
  - **Producer**: Client that sends messages to Kafka
  - **Consumer**: Client that reads messages from Kafka
  - **Consumer Group**: Set of consumers sharing the reading of messages
  - **Offset**: Position of a message within a partition
  - **Replication**: Copies of partitions for durability
- Kafka often sits between producers and consumers, allowing different applications to communicate asynchronously
- Kafka allows applications to send (produce) messages to a topic, and other applications can receive (consume) those messages.
