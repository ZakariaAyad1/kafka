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



📁 Admin Portal Walkthrough
URL (default): http://localhost:9090
Login: admin / admin

🧱 1. Realm
A realm isolates a group of clients, users, and roles.

Go to Realm Selector > Create Realm

Name it: whatsapp-clone

📱 2. Clients
A client is an app that uses Keycloak (like Angular or Spring Boot)

Go to Clients > Create Client

Name: angular-client

Type: public (no secret)

Redirect URI: http://localhost:4200/*

➡️ You’ll use this in Angular

👥 3. Users
Go to Users > Add User

Fill:

Username: zak

Email, First name, etc.

Then:

Go to Credentials tab

Set password and uncheck Temporary

🎭 4. Roles
Roles define access (like USER, ADMIN)

Go to Realm Roles > Create Role

Create: USER, then ADMIN

Then:

Go to user profile > Role Mappings

Assign USER to your user

⚙️ 5. Clients for Backend
Create another client: spring-backend

Type: confidential

Turn on Service accounts

Copy the generated client secret

This client will be used by Spring Boot to verify tokens.

🔐 Tokens
When Angular logs in:

It gets a JWT access token

This token is signed and contains:

User info (email, username)

Realm roles

Expiry time

Spring Boot:

Validates the token

Extracts roles

Authorizes access to endpoints
