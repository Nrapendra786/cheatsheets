# Here's a cheatsheet to help you master Apache Kafka, covering the essentials for becoming an expert:

## 1. Kafka Basics
## Topics: Logical channels for message distribution. Each topic is divided into partitions.
## Partitions: Units of parallelism in Kafka. Messages within a partition are ordered.
## Producers: Publish messages to topics.
## Consumers: Read messages from topics.
## Brokers: Kafka servers that store and serve messages.
## Cluster: Multiple brokers working together.
## Replication: Duplicates data across brokers for fault tolerance.

## Zookeeper: Manages broker metadata and leader elections (replaced by Kafka Raft in newer versions).
## 2. Key Kafka Configuration Settings
## Producer Configs:

## acks: Controls message durability. Use all for maximum reliability.
## retries: Number of retries for failed sends.
## linger.ms: Adds delay for batching.
## compression.type: Use snappy or gzip for message compression.
## Consumer Configs:

## group.id: Defines a unique group of consumers.
## auto.offset.reset: Use earliest to start from the beginning or latest to continue.
## enable.auto.commit: Set to false for manual offset management.
## max.poll.records: Limits the number of records returned in a poll.
# 3. Advanced Kafka Concepts
## Offset Management: Tracks the last consumed record. Use Kafka’s __consumer_offsets topic for managing.
## Consumer Groups: Allow scaling by assigning partitions among consumers.
## Idempotent Producers: Ensure exactly-once message delivery.
## Transactions: Ensure atomic writes across topics/partitions using Kafka transactions.
## Log Compaction: Retain only the latest version of a message based on a unique key, useful for "changelog" type topics.
# 4. Schema Management with Apache Avro and Schema Registry
## Schema Evolution: Use Avro with Schema Registry to manage changes in message schemas.
## Compatibility: Schema Registry supports backward, forward, and full compatibility to avoid breaking consumers when schemas change.
# 5. Performance Tuning Tips
## Partitions: Balance partitions for parallelism but avoid excessive partition counts to reduce broker load.
## Compression: Use message compression to reduce network usage.
## Batch Size: Increase batch.size for producers to improve throughput.
## Replication Factor: For critical data, use a replication factor of 3 (minimum 2).
## Num of Brokers: Scale brokers based on expected load and required fault tolerance.
# 6. Error Handling and Retries
## Dead Letter Queue (DLQ): Route messages that fail processing to a special DLQ topic.
## Retry Strategies: Configure retry strategies using exponential backoff, especially for transient errors.
## Consumer Lag Monitoring: Track lag to prevent processing delays and ensure prompt handling of large backlogs.
# 7. Kafka Stream Processing with KSQL and Kafka Streams
## Kafka Streams: Build real-time stream processing apps using Kafka’s native stream library.
## Stateless Operations: e.g., filter, map.
## Stateful Operations: e.g., aggregate, join, windowed.
## KSQL: SQL-like syntax for real-time stream processing.
# 8. Observability and Monitoring
## Key Metrics:
## Producer: record-send-rate, record-size-avg, request-latency-avg.
## Consumer: records-lag-max, records-consumed-rate, commit-latency-avg.
## Broker: under-replicated-partitions, request-handling-time, isr-shrinks.
## Tools:
## Prometheus & Grafana: Collect and visualize Kafka metrics.
## Confluent Control Center or Burrow: Monitor consumer lag.
## Kafdrop: GUI for monitoring Kafka clusters.
# 9. Security Best Practices
## Authentication:
## Use SASL (e.g., SASL_PLAINTEXT, SASL_SSL) to authenticate clients.
## Authorization:
## Use ACLs (Access Control Lists) to define which users/groups can access topics.
## Encryption:
## Use SSL encryption for data-in-transit.
## Audit Logs: Enable auditing to track access and operations.
# 10. Kafka with Docker and Kubernetes
## Docker: Use ready-to-deploy Kafka and Zookeeper Docker images.
## Kubernetes: Use Kafka operators like Strimzi or Confluent Operator to manage Kafka on K8s.
## Persistent Volumes: Set up Persistent Volume Claims (PVCs) for storage.
## Scaling: Configure Horizontal Pod Autoscaling for Kafka consumers.
# 11. Troubleshooting Common Issues
## Message Loss: Use replication, increase acks, and enable idempotent producers.
## Consumer Lag: Scale consumer instances or investigate processing bottlenecks.
## Serialization Errors: Ensure schema compatibility and use proper deserializers.
## High Latency: Increase broker memory, optimize producer configs, and manage partitions effectively.
# 12. Useful CLI Commands
## List Topics: kafka-topics.sh --list --bootstrap-server <broker-address>
## Create Topic: kafka-topics.sh --create --topic <topic-name> --partitions <num> --replication-factor <num> --bootstrap-server <broker-address>
## Describe Topic: kafka-topics.sh --describe --topic <topic-name> --bootstrap-server <broker-address>
## Produce to Topic: kafka-console-producer.sh --topic <topic-name> --bootstrap-server <broker-address>
## Consume from Topic: kafka-console-consumer.sh --topic <topic-name> --from-beginning --bootstrap-server <broker-address>
## Mastering these areas will give you a strong foundation and equip you to handle both basic and advanced Kafka use cases.
