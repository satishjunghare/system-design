# # What is Distributed System
A distributed system is a collection of independent computers (or nodes) that work together as a single system to achieve a common goal. These computers communicate and coordinate their actions through a network, sharing resources, data and workloads.

## Key Characteristics of Distributed System
1. **Multiple nodes:** Mltiple nodes are using in distributed systems.
2. **Communication via a network:** All nodes communicates via communication protocols like TCP/IP, HTTP, gRPC or message queue like Kafka, RabbitMQ, etc.
3. **No shared clock:** Each node has their own local clock which can lead to event ordering challenges.
4. **Resource sharing:** All nodes share resources, including files, databases and processing power.
5. **Fault tolerance:** All nodes work together to handle situations like node failures to not hampering the operation.
6. **Scalability:** We can add or remove nodes from network depends on the requirements to handle the workload.
7. **Transparency:** They should hide the complexities like location, replications and migrations from the end user.

## Examples of Distributed Systems
1. Internet: 
2. Cloud Computing Platforms:
3. Content Delivery Networks:
4. Blockchain Networks:
5. Distributed Databases:
6. Microservice Architecture:

## Advantages of Distributed Systems
1. Scalability:
2. Fault Tolerance:
3. Resource Sharing:
4. Geographical Distribution:
5. High Availability:

## Disadvantages of Distributed Systems
1. Complexity:
2. Latency:
3. Data Consistency Issues:
4. Security Risks:
5. Synchronization:

## Key Challenges in distributed Systems
1. CAP Theorem:
2. Concurrency Control:
3. Fault Detection and Recovery:
4. Data Replication:
5. Latency and Bandwidth Constraints:

## Real-World Use Cases
1. Netflix
2. Uber
3. Amazon DynamoDB
4. Google Search
5. Bitcoin and Blockchain Networks




<br>

# # Data Consistency
Way to measure how recent and up to date a peace of data is. If you get a peace of data which reflects all of the updates, we call it highly consistent. And if we get stale data, we call it inconsistent or weakly consistent.

## Linearizable Consistency
Ensures that every read returns the most recent write. The system behaves as if all operations occur in a single, global order, even though they are may be executed across multiple nodes.

### Use Cases:
- Financial transactions
- Real-time collaborative tools (e.g. Google Docs)
- Systems requiring strong data correctness guarantees.

### Drawbacks:
- High latency due to synchronization requirements across nodes
- Reduced availability during network partitions

## Eventual Consistency
Eventual consistency guarantees that, if no new updates are made to a data item, eventually all nodes will converge to the same value. Imagine a social media post. When wyou post an update, some of your friends might see it instantly, while others may see it after a delay. Eventually, everyone will see the same post.

### How it Works:
- Updates are propogated asynchronously.
- Over time, all nodes will converge to the same value.
- There is no guarantee about the order or immediate consistency after a write.

### Use Cases:
- social media feeds
- DNS systems
- Caching layers (e.g. Redis, Memcached)

### Trade-offs:
- Potential stale reads

## Causal Consistency
Gurantees that causally related operations are seen in the same order by all nodes, but operations that are independent of each other can be seen in different orders. 

### How it Works:
- If operation A causally affects operation B, every node must see A before B.

### Use Cases:
- Chat application (e.g. WhatsApp, Slack)
- Collaborative editing tools (e.g. Etherpad)
- Multi-user real-time applications

### Trade-offs:
- More complex to implement than eventual consistency.
- Additional metadata (e.g. vector clocks) is needed to track casual relationships.

## Quorum Consistency
Quorum consistency is a consistency model used in distributed databases and systems to ensure a balance between data availability, fault tolerance, and consistency.