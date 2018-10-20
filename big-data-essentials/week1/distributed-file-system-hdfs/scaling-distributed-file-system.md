# Scaling Distributed File System

## Approaches

- Scale-up: Bigger drive
- Scale-out: Buy more nodes

## GFS

Scalable file system

### GFS Key Components

- Components failures are a norm (-> replication)
- Even space utilization
- write-once-read-many (no updates)
- Metadata: properties of data
- HDFS: is an open source implementation of GFS made in Java

### HDFS

#### How to read data from HDFS

- Request the namenode the fileblokcs location

- You will get data from the closest machine
  - Data in same machine: 0
  - Data in same rack: 2
  - Data from another rack: 4
  - Data from another data center: 6

#### How to write data into HDFS

- First replica is written in the same node, if it's written from a datanode machine, otherwise is chosen by random
- Second replica in a different rack
- Different machine from the sae rack
- Other replicas are placed on random nodes in the cluster
