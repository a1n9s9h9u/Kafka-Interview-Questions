## Kafka Interview Questions

#### What is Kafka?

Apache Kafka is a streaming platform that is free and open-source. It's a versatile tool for working with data streams that may be applied to a variety of scenarios. Kafka is a distributed system, which means it can scale up as needed. All you have to do now is add new Kafka nodes (servers) to the cluster. Kafka can process a large amount of data in a short amount of time. It also has low latency, making it possible to process data in real-time.

#### What are some of the features of Kafka?

Kafka is a messaging system built for high throughput and fault tolerance.

Kafka has a built-in patriation system known as a Topic.

Kafka provides a queue that can handle large amounts of data and move messages from one sender to another.

Kafka can also save the messages to storage and replicate them across the cluster.

For coordination and synchronization with other services, Kafka collaborates with Zookeeper.

Apache Spark is well supported by Kafka.

#### What are the traditional methods of message transfer? How is Kafka better from them?

#### Message Queuing:- 

A point-to-point technique is used in the message queuing pattern. A message in the queue will be destroyed once it has been consumed, similar to how a message is removed from the server once it has been delivered in the Post Office Protocol.

If a network problem delays a message's delivery, such as if a consumer is unavailable, the message will be held in the queue until it can be sent. This means that messages aren't always sent in the same order. Instead, they are given on a first-come, first-served basis, which can improve efficiency in some situations.

#### Publisher - Subscriber Model:- 

The publish-subscribe pattern entails publishers producing ("publishing") messages in multiple categories and subscribers consuming published messages from the various categories to which they are subscribed. Unlike point-to-point texting, a message is only removed once it has been consumed by all category subscribers.

#### Following are the benefits of using Kafka over the traditional messaging transfer techniques:

Scalable: A cluster of devices is used to partition and streamline the data thereby, scaling up the storage capacity.

Faster: Thousands of clients can be served by a single Kafka broker as it can manage megabytes of reads and writes per second.

Durability and Fault-Tolerant: The data is kept persistent and tolerant to any hardware failures by copying the data in the clusters.

#### What are the major components of Kafka?

#### Topic

A Topic is a category or feed in which records are saved and published. Topics are used to organize all of Kafka's records. Consumer apps read data from topics, whereas producer applications write data to them. Records published to the cluster remain in the cluster for the duration of a configurable retention period.

#### Consumers

Kafka keeps records in the log, and it's up to the consumers to keep track of where they are in the log (the "offset"). As messages are read, a consumer typically advances the offset in a linear fashion. The consumer, on the other hand, is in charge of the position, as he or she can consume messages in any order. When reprocessing records, for example, a consumer can reset to an older offset.

#### Producers

A Kafka producer is a data source for one or more Kafka topics that optimizes, writes, and publishes messages. Partitioning allows Kafka producers to serialize, compress, and load balance data among brokers.

#### Consumer group

Data is read by consumers by reading messages from topics to which they have subscribed. Consumers will be divided into groups. Each consumer in a consumer group will be responsible for reading a subset of the partitions of each subject to which they have subscribed.

#### Kafka broker

A Kafka broker is a server that works as part of a Kafka cluster (in other words, a Kafka cluster is made up of a number of brokers). Multiple brokers typically work together to build a Kafka cluster, which provides load balancing, reliable redundancy, and failover. The cluster is managed and coordinated by brokers using Apache ZooKeeper. Without sacrificing performance, each broker instance can handle read and write volumes of hundreds of thousands per second (and gigabytes of messages). Each broker has its own ID and can be in charge of one or more topic log divisions.

#### Explain the four core API architecture that Kafka uses.

The Producer API in Kafka allows an application to publish a stream of records to one or more Kafka topics.

An application can subscribe to one or more Kafka topics using the Kafka Consumer API. It also enables the application to process streams of records generated in relation to such topics.

The Kafka Streams API allows an application to use a stream processing architecture to process data in Kafka. An application can use this API to take input streams from one or more topics, process them using streams operations, and generate output streams to transmit to one or more topics. The Streams API allows you to convert input streams into output streams in this manner.

The Kafka Connector API connects Kafka topics to applications. This opens up possibilities for constructing and managing the operations of producers and consumers, as well as establishing reusable links between these solutions. A connector, for example, may capture all database updates and ensure that they are made available in a Kafka topic.

#### What do you mean by a Partition in Kafka?

Kafka topics are separated into partitions, each of which contains records in a fixed order. A unique offset is assigned and attributed to each record in a partition. Multiple partition logs can be found in a single topic. This allows several users to read from the same topic at the same time. Topics can be parallelized via partitions, which split data into a single topic among numerous brokers.

#### Replication in Kafka

Replication in Kafka is done at the partition level. A replica is the redundant element of a topic partition. Each partition often contains one or more replicas, which means that partitions contain messages that are duplicated across many Kafka brokers in the cluster.

#### Can we use Kafka without Zookeeper?

Kafka can now be used without ZooKeeper as of version 2.8. 

#### Explain the concept of Leader and Follower in Kafka.

In Kafka, each partition has one server that acts as a Leader and one or more servers that operate as Followers. The Leader is in charge of all read and writes requests for the partition, while the Followers are responsible for passively replicating the leader. In the case that the Leader fails, one of the Followers will assume leadership. The server's load is balanced as a result of this.

#### Why is Topic Replication important in Kafka?

Topic replication is critical for constructing Kafka deployments that are both durable and highly available. When one broker fails, topic replicas on other brokers remain available to ensure that data is not lost and that the Kafka deployment is not disrupted.

#### What is the maximum size of a message that Kafka can receive?

By default, the maximum size of a Kafka message is 1MB (megabyte). The broker settings allow you to modify the size.

#### What does it mean if a replica is not an In-Sync Replica for a long time?

A replica that has been out of ISR for a long period of time indicates that the follower is unable to fetch data at the same rate as the leader.

#### How do you start a Kafka server?

Firstly, we extract Kafka once we have downloaded the most recent version. We must make sure that our local environment has Java 8+ installed in order to run Kafka.

#### The following commands must be done in order to start the Kafka server and ensure that all services are started in the correct order:

Start the ZooKeeper service by doing the following:
```powershell
$bin/zookeeper-server-start.sh config/zookeeper.properties
```
To start the Kafka broker service, open a new terminal and type the following commands:
```powershell
$ bin/kafka-server-start.sh config/server.properties
```
#### What do you mean by geo-replication in Kafka?

Geo-Replication is a Kafka feature that allows messages in one cluster to be copied across many data centers or cloud regions. Geo-replication entails replicating all of the files and storing them throughout the globe if necessary.

#### What are some of the disadvantages of Kafka?

Brokers and consumers reduce Kafka's performance when dealing with huge messages by compressing and decompressing the messages. This has an impact on Kafka's throughput and performance.

#### Describe partitioning key in Kafka.

In Kafka terminology, messages are referred to as records. Each record has a key and a value, with the key being optional. For record partitioning, the record's key is used. There will be one or more partitions for each topic.

Partitioning is done using the record's key. By default, Kafka producer uses the record's key to determine which partition the record should be written to. The producer will always choose the same partition for two records with the same key.
