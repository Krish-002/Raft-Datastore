# Distributed Key-Value Database Project

## High-Level Approach

This project involves building a distributed, replicated key-value datastore using a simplified version of the Raft consensus protocol. The goal is to maintain strong consistency guarantees across multiple replicas in a simulated hostile network environment. The system supports basic `put(key, value)` and `get(key)` operations, which are fundamental for any key-value storage system. The implementation is in Python, taking advantage of its simplicity and robust standard libraries, particularly for handling network communications and JSON data.

## Challenges Faced

- **Understanding Raft Protocol**: Grasping the nuances of the Raft consensus algorithm was challenging, especially in ensuring correct leader election and reliable log replication across network partitions.
- **Network Simulations**: Dealing with an unreliable network in the simulation posed significant difficulties in maintaining consistent state across replicas.
- **Concurrency and Timing Issues**: Implementing and managing timeouts, elections, and heartbeat messages to avoid split-brain scenarios in the cluster was complex due to the asynchronous nature of network communications.
- **Debugging Distributed Systems**: Debugging was particularly tough because issues had to be traced across multiple interacting replicas, often requiring careful analysis of logs and message flows.

## Key Features and Properties

- **Fault Tolerance**: The system handles node failures gracefully by ensuring that the datastore continues to function as long as a majority of the nodes are operational.
- **Election Safety**: Implemented mechanisms to ensure that there is at most one leader per term, in accordance with the Raft specification.
- **Log Replication**: Efficiently handles log replication to keep all nodes consistent with the leader's log, even in the presence of network failures.
- **Robust Client Operations**: Clients can consistently put and get values with confidence, as operations are processed correctly following the principles of Raft.

## Testing the Code

- **Unit Testing**: Each component of the code (like leader election, log replication, client request handling) was tested individually to verify its correctness.
- **Integration Testing**: The components were tested together to ensure they work as expected in a more realistic, integrated environment.
- **Simulation Environment**: Utilized the provided simulator to create a network of replicas and simulate client interactions along with network failures. This helped in validating the consistency and availability properties of the datastore.
- **Performance Metrics**: Monitored and tuned the system to improve transaction latency and reduce the overhead caused by Raft's protocol operations.

## Conclusion

This project provided a comprehensive understanding of how distributed systems manage data consistency and availability in the face of network partitions and node failures. The challenges faced pushed for a deeper understanding of distributed algorithms and their practical implications in real-world systems.