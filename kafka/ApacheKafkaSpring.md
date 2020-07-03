# APACHE KAFKA AND SPRING FRAMEWORK
### Apache kafka installation
- We will need to go to the oficial website wich is [here](https://kafka.apache.org/downloads). We will need to download the version that is recommended in the documentation.
- Download the binaries, and unzip it.
### Why apache kafka
- Messaging is one of the popular trend in sharing the data between the applications/systems real time.
- There are two popular legacy messaging solutions **Publish-Subscribe(Topic) and Queue**
  - **Publish-Subscribe:** Messages are published to a message broker and message will be distributed to all of the consumers. Topics retain messages only as long as it takes to distribute them to current subscribers. The subscribe must continue to be active for it to consume the messages.
  - **Queue:** Messages are published to a queue and the consumer will read from it. Limitation is you can have only one consumer queue.
- There is always a limit on the size of the message because larger message may end up breaking the message broker or make the broker to perform slower.
- Legacy Messaging solution have zero **Fault-Tolerance**
- **Fault Tolerance - Scenario 1:**
  - We have a consumer reads the message and it process the messages and store the attibute of the message in the DB.
  - Once the consumer reads the message and then it process the message but the back end DB is down or there is bug in the consumer code. Under this scenario there is no way the consumer can read this same message again from the message broker.

### What is Apache Kafka?
- Apache kafka is a scalable, reliable, high volume and high throughput distributed messaging system.
- Apache kafka is mainly used for sharing high volume data from one system to another system in real time and retention of data.
- LinkedIn started their development in 2009 and implemented in 2010 as their architecture solution.
- It was outsourced to Apache software foundation by 2011. Currently this is one of the mostly used tools in Apache software foundation.

##### Advantages
- Messages are not removed from the topic as soon as the consumers consume it.
- Kafka is Horizontally scalable.
- Kafka has stronger ordering guarantees than a traditional messaging system.
- Kafka can handle high volume and it has very high throughput.
- Kafka design supports loosely coupled Producers and Consumers.
- Kafka can also be used as a storage system.


### Core Internals of Apache Kafka
##### Zookeeper and Kafka Broker
- Go to the binaries folder
- Edit ```server.properties``` file
- Edit line ```advertised.listeners=PLAINTEXT://<yourhost>:<port>```
- Then launch the kafka broker.

#### Kafka Topics
- Topic is an Entity in kafka with a name, it generally lives in a kafka broker.
- Even if the messages are consumed, it will still be there for some 'retention time'

##### Partitions, Producers, Consumers and Retention Period in Topic
- **<ins>Partition is where the message lives inside the topic</ins>**
  - Each partition is an ordered, inmutable sequence of records.
  - Each record is assigned a sequencial number called offset.
  - Each partition is independent of each other
  - Ordering is guaranteed only at the partition level.
  - Partition continuosly grows as new records are produced.
  - All the records are persisted in a commit log in the file system where Kafka is installed.
- **<ins>Each topic will be created with one or more partitions</ins>**

- The retention period of records in Kafka is configurable
- The **default retention period** is **7 days**. The retention period is specific to topic. So in the Cluster each topic can have their own retention period.
- The retention attribute is available in the server.properties of the apache kafka distribution.
  - The attribute is **log.retention.hours=168**
- Lets us say the retention period is one day then in this case then record will be discarded after one day to free up some space in the cluster.
- Irrespective of all the consumers have consumed the message, the record will sit in the cluster until the retention period expires.
- The performance of Kafka is consistent with respect to data size so holding the data for a long time is not an issue here.

##### Setting up Zookeeper & Kafka Broker
- We can find all the required steps [here](https://github.com/franco148/dev-ops-notes/blob/master/kafka/SetupKafka.md).

##### Sending Kafka Messages With Key and Value
- Kafka Message sent from producer has two properties
  - Key (optional): 
  - Value: 

##### Consumer Offsets
- Consumer have three options to read (this is helpful when we want to read from a specific message (offset))
  - from-beginning
  - latest
  - specific offset
- Consumer offsets behaves like a bookmark for the consumer to start reading the messages from the point it left off.























