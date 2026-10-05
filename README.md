# Distributed File System


## Installation 

## About

This project entails designing and implementing a containerized, chunk-based Distributed File System utilizing a master node and chunk servers independently operating in Docker. An additional Docker container will function as a client/benchmark node, which we will use to quantify the metrics of our system and support parallel file uploads and downloads. The master node will oversee managing chunk data mapping and leasing to ensure we meet our desired replication factor. The individual chunk servers will function as independent nodes with peer-to-peer data pipelining. The initial plan is to start with a replication factor of 2 with 3 chunk servers, but both replication factor and chunk server quantity should be easily scalable within the project implementation. 

The system will possess an append-mostly consistency model to mitigate diverging replicas and expensive rewrites. A primary-replica lease mechanism will also be implemented to prevent the master node from becoming a network bottleneck. Heartbeat failure detection will be used to detect node failure and prevent it from further hindering the system. Synthetic network fault injection via Linux traffic control will be used to simulate un-ideal network conditions to validate fault tolerance and recovery time. 

## Authors

Ethan Buenting, Ethan Van Caster, and Sullivan Hart 