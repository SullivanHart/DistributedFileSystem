# Distributed File System


## Installation

### Requirements

- Docker Engine
- Docker Compose v2


### Linux setup (Ubuntu)

If Docker and Compose are not already installed:

```
sudo apt update
sudo apt install docker.io docker-compose-v2
```

Optional: allow Docker commands without `sudo`:

```
sudo usermod -aG docker "$USER"
newgrp docker
```

The Docker group grants administrative access through Docker. If you skip this step, prefix the Docker commands below with `sudo`.

### Start the system

From the project directory:

```bash
docker compose up -d
docker compose ps
```

### Stop the system

```bash
docker compose down
```

## About

This project entails designing and implementing a containerized, chunk-based Distributed File System utilizing a master node and chunk servers independently operating in Docker. An additional Docker container will function as a client/benchmark node, which we will use to quantify the metrics of our system and support parallel file uploads and downloads. The master node will oversee managing chunk data mapping and leasing to ensure we meet our desired replication factor. The individual chunk servers will function as independent nodes with peer-to-peer data pipelining. The initial plan is to start with a replication factor of 2 with 3 chunk servers, but both replication factor and chunk server quantity should be easily scalable within the project implementation. 

The system will possess an append-mostly consistency model to mitigate diverging replicas and expensive rewrites. A primary-replica lease mechanism will also be implemented to prevent the master node from becoming a network bottleneck. Heartbeat failure detection will be used to detect node failure and prevent it from further hindering the system. Synthetic network fault injection via Linux traffic control will be used to simulate un-ideal network conditions to validate fault tolerance and recovery time. 

## Authors

Ethan Buenting, Ethan Van Caster, and Sullivan Hart 