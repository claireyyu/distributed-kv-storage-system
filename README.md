# Distributed Key-Value Storage System

This is a distributed key-value storage system that implements the Raft consensus algorithm for high availability and strong consistency. It supports leader election, log replication, snapshotting, and dynamic changes to cluster membership. The system is optimized for performance with features like asynchronous Apply, ReadIndex, FollowerRead, and Prevote to reduce leader elections.

## Features

- **Raft Consensus Algorithm**: Ensures strong consistency with leader election, log replication, and snapshotting.
- **Consistent Hashing**: Partitions data across multiple Raft groups, allowing for seamless migration.
- **Optimized Reads**: Uses asynchronous Apply, ReadIndex, and FollowerRead for improved performance.
- **High Performance**: Handles 20,000 queries per second with a P99 latency of 800ms.

## Quick Start

To deploy a 3-instance Raft cluster locally, use the provided script:

```bash
cd distributed-kv-example && sh deploy.sh
```

The script sets up three instances (example1, example2, and example3) under the `env` directory. A client directory is also created to test read/write operations on the Raft cluster.

### Write Operation

```bash
cd env/client
./bin/run_client.sh "list://127.0.0.1:8051,127.0.0.1:8052,127.0.0.1:8053" hello world
```

### Read Operation

```bash
./bin/run_client.sh "list://127.0.0.1:8051,127.0.0.1:8052,127.0.0.1:8053" hello
```
