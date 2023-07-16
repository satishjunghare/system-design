# System Design Interview Guide

### Step 1 - Understand the Problem and Establish Design Scope**
1. Functional requirements: Defines the functional aspects
2. Non-Function requirements: Availability, Latency, Consistency etc.
3. Additional requirements

### Step 2 - Back of The Envelope Estimation
1. Scale
   1. Number of daily active users
   2. Incoming trafic requests: QPS/TPS
   3. Size of database
2. Partitioning
   1. Number of partitions
3. Load Balancing
4. Caching
   1. Size of cache

### Step 3 - Purpose High-level Design and Get Buy-in
1. API design
2. Data model
   1. Read/write ratio
   2. Data schema
      1. Business table
      2. Indexing
3. High level design

### Bottlenecks/Tradeoffs
1. Single point of failure
2. Enough replicas to store data
3. Monitoring and performance
4. Auto scaling
5. Error scenarios

