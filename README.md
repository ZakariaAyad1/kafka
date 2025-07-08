# kafka

Apache Kafka is an open-source distributed event streaming platform used to build real-time data pipelines and streaming applications. It was originally developed by LinkedIn and is now maintained by the Apache Software Foundation.

🔧 What does Kafka do?
Kafka lets you:

Publish (write) data to topics (channels).

Subscribe (read) data from topics.

Store streams of records in a fault-tolerant way.

Process streams of records in real-time.

🔁 Kafka Core Concepts
Concept	Description
Producer	App that sends (publishes) data to Kafka topics.
Consumer	App that reads (subscribes to) data from Kafka topics.
Topic	A category/channel where records are sent (like a queue).
Partition	Topics are split into partitions to allow parallel processing.
Broker	Kafka server that stores data and handles requests.
Consumer Group	A group of consumers that share the load of reading from a topic.
ZooKeeper (legacy)	A service Kafka used to manage its cluster metadata (newer versions use KRaft mode instead).

✅ Why Use Kafka?
High throughput and low latency.

Handles millions of messages per second.

Works great for microservices, event-driven architectures, real-time analytics, and log aggregation.

Scalable, durable, and fault-tolerant.

📌 Example Use Cases
Logging systems (e.g., collect logs from multiple servers).

Event sourcing in microservices.

Real-time analytics dashboards.

Order tracking systems in e-commerce.

Stream processing using Kafka Streams or Apache Flink.



# Apache Kafka – Architecture Overview

Apache Kafka is a distributed event streaming platform capable of handling trillions of events per day. It is designed for high throughput, fault tolerance, horizontal scalability, and real-time data processing.

---

## 📌 Kafka Architecture Diagram


graph LR
    A[Producer(s)] -->|Write messages| B[Kafka Broker(s)]
    B --> C1[Topic: user-events]
    B --> C2[Topic: order-events]
    C1 -->|Partition 0| D1[Kafka Broker 1]
    C1 -->|Partition 1| D2[Kafka Broker 2]
    C2 -->|Partition 0| D1
    C2 -->|Partition 1| D2
    D1 --> E[Consumer Group A]
    D2 --> E
    E -->|Read messages| F[Stream Processor / Application]



🧠 What Is Keycloak?
Keycloak is an open-source Identity and Access Management (IAM) solution that provides:

✅ SSO (Single Sign-On)
✅ Authentication (Login, Registration)
✅ Authorization (Role-based access control)
✅ OAuth2, OpenID Connect, SAML
✅ Social logins (Google, Facebook, etc.)
