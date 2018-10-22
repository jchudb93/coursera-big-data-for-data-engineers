# Block and replica states

## Block and replica

* Replica is a physical data storage on a data node. There are several replicas with the same content on different data nodes.
* block is a meta*information storage on a name node and provides information about replica's locations and their states.

## Replica and block states

* If replica is finalized state then it means that the content of this replica is cool and icy and the meta*information for this block on name node is aligned with all the corresponding replica's states and data. You can access data with any problem.

* RBW stands for **Replica Being Written.It's the state when the last block of an open file or a file which is reopened for appending**. During this state, different data nodes can return different sets of bytes and meta*information may not also match. In case of failure data node will try to preserve as many bytes as possible.

* RWR stands for Replica Waiting to be Recovered. **This data will be discarded or will participate in a special recover process called lease recovery if the client also dies**. Usually happens with client failure.

* HDFS client **requests a lease from a name node to have an exclusive access to write or append data to a file**. In case of HDFS client lease expiration, replica transition to a **RUR state, Replica Under Recovery**. Lease expiration usually happens during the client's site failure.

* As data grows and different nodes are added or removed from a cluster, data can become unevenly distributed over the cluster nodes. A Hadoop administrator can spawn a process of data re-balancing or an increasing factor can be requested. This new replicas are called **TEMPORARY**. It's the same as RBW except the fact this data is invisible to users unless it's finalized

* Blocks are stored in memory. As soon as the **user opens a file for writing or appending, name node also creates the corresponding block with the under_construction state**.

* Name node blocks keep track of right pipeline. It means that **it contains information about all RBW and RWR replicas**.

* The under_construction block transitions to a commited state when a client successfully requests name node to close a file or to write a new consecutive block of data.

## The recovery process

* During the block recovery process Name Node has to ensure that all of the corresponding replicas of a block will transition to a common state logically and physically. All the correspondent replicas should have the same on disk content. 