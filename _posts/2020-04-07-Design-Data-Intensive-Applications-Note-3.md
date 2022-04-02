---
layout: post
category : Learning
tagline: 
thumbnail-img: /assets/img/ddia.jpg
tags : [Learning, Data]
---

## Design Data-Intensive Applications

### CH9 Consistency and Consensus
  * Linearizability: make a system appeart as if there were only one copy of data and all operations are atomic
    * Linearizability vs Serializability
    * CAP theorem
  * Ordering Guarantees
    * Linearizability: total order of operations
    * Causality defines partial order
    * Linearizability is stronger than causal consistency
    * Total order broadcast
  * Distributed Transactions and Consensus
    * Atomic commit
    * two-phase commit: use coordinator
    * fault-tolerant consensus algorithms: VSR, Paxos, Raft and Zab, total order algorithms

### CH10 Batch Processing
  * Unix tools: awk, sed, grep, sort, uniq, xargs
  * MapReduce and distributed filesystems
    * Reduce-Side join
    * Map-Side join
      * broadcast hash join
      * partitioned hash join
      * map-side merge join
    * Batch Process Output
      * Build search index
      * Key-value stores
    * Map reduce vs MPP: handling of faults and use of memory/disk 
  * Beyond MapReduce
    * Map reduce materilize intermediate state, other engines:Spark, Tez and Flink
    * Pregel processing model to process graph data

### CH11 Stream Processing
  * Messaging Systems: publish/subscribe model
    * direct messaging from producers to consumers
    * Message brokers
      * AMQP/JMS-style message broker
      * log-based message brokers: Kafka, Kinesis etc., taking ideas from db
    * Change Data Capture: mutable
    * Event Sourcing: record immutable events
  * Processing Streams
    * Event time vs Processing Time
    * Stream-stream join, stream-table join, table-table join
    * fault-tolerance: exactly-once semantics
      * Microbatching: Spark Streaming; checkpointing: Apache Flink

### CH12 The Future of Data Systems 
  * Data Integration
    * Unifying batch and stream processing
  * Unbundling Databases
  * Ensure processing is correct
  * Predictive analytics bias and privacy
