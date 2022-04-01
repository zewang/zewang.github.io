---
layout: post
category : Learning
tagline: 
tags : [Data]
---
{% include JB/setup %}

## Design Data-Intensive Applications

### CH5 Replication
  * Single-leader replication, asynchronous replication is widely used
    * Statement-based replication
    * Write-ahead log (WAL) shipping
    * Logical (row-based) log replication
    * Trigger-based replication
  * Problems with Replication Lag
    * implement read-after-write consistency
    * Monotonic Reads, always read from the same replica
    * Consistent Prefix Reads 
  * Multi-leader replication
    * Use Case: multi-datacenter operation, clients with offline operation, collaborative editing
    * Handling Write Conflicts: avoid by routing to same datacenter
    * Replication Topology: all-to-all
  * Leaderless replication: Amazon Dynamo
    * Quorum for read and write

### CH6 Partitioning
  * Partition by Key Range
  * Partition by Hash of Key
  * Secondary index
    * local index: document-partitioned index, each partition maintains its own secondary indexes
    * global index: term-partitioned index, can be partitioned differently from the primary key index
  * Rebalancing Partitions
  * Routing requests
    * which component makes the routing decision
      * each node
      * routing tier: zookeeper maintains the authoritative mapping of partitions to nodes
      * client
  
### CH7 Transactions
  * ACID: Atomocity, Consistency, Isolation and Durability
    * A and C describes what the database should do if a client makes several writes within the same transaction
    * Isolation
      * READ COMMITTED isolation guarantees no dirty reads and no dirty writes, lock to prevent dirty writes, remembers both old committed value and new value by write lock
      * SNAPSHOT isolation to address read skew: MVCC, multi-version concurrency control
      * lost updates
      * write skew, phantom addressed by materializing conflicts
    * Serialization isolation
      * Actual Serial Execution
      * Two-phase locaking
      * Serializable Snapshot Isolation 
  * BASE: Basically Available, Soft state and Eventual consistency

### CH8 The Trouble with Distributed Systems
  Partial failures can occur 
  * Unreliable Networks
  * Unreliable Clock
  * Process Pause
  * Syetem model
    * timing assumptions: sychronous model, partially synchronous model, asynchronous model
    * node failures: crash-stop faults, crash-recovery faults, byzantine(arbitrary) faults 
  First detect the faults(timeouts), tolerate (get quorum to agree on)