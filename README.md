## Real Time Use Cases @Uber

## Scalability Challenges
* Scaling Data: PetaBytes  of Data
* Scaling Use Cases
* Scaling Users 

## Layered Abstractions
* Storage: Blog Storage Interface, Read After Write Consistency(HDFS)
* Stream: Pub-sub interface, at least one semanatices(Apache Kafa)
* Compute: Works with Storage and Stream and provide at least one semanttices (Flink)
* OLAP (Pinot)
* SQL: Can work with both compute and OLAP (Presto)
* Programming API: For advanced users
* Metadata: For other storage

## Apache Kafka For Streaming Data
### Use Cases for Uber
* Pub/Sub
* Stream Processing
* Change Data Capture
* Ingestion into Data Lake
* Logging

### Cluster Federation
- Simple Discovery
- Scale Horizontally
- Tolerate single-cluster failure

### Dead Letter Queue(DLQ)
- Non-blocking and lossless events processing

### Consumer Proxy
- Proxy Layer in the middle
- Enhancment Over Kafka Protocol
- Take complexity away from receiver services
- Centralize management

## Apache Flink for Stream Processing
- Known for high-throughput, low-latency and fault-tolerant
- Fink as a Service(FaaS)
- FlinkSQL
5.1) FlinkSQL

## Apache Flink @Uber - Unified Platform
- Heterogeneous Systems
* Job Type(SQL, FaaS, DSL)
* Flink Version
* Cluster Management System
- High Availability
* Deployment Flow
* Dependent Systems
- Deployment Efficiency
* Minimum Donwtime during upgrade
* Disaster Recovery
* Relaibility of Ecosystem

## Apache Pinot
- Distributed, columan database
- Use cases at Uber
* User-Facing Analystic


## Apache Pinot - Upserts
* First real-time OLAP to support upsert
* Challenge: Data Stored as immutable segments
* Data Partioning to share nothing


## Apache Pinot
- Full SQL Support 

## All Active Strategy
### Active-Active
* Replication
### Active-Passive
### Data Backfill
* Bootstrapping with historial data
* Reprocessing Due to 
  *  Bugs
  *  Change in computation logic
* Required for all the layers in the stack


## Lesson Learned
* Open source Adoption
  * Pros: Reduce time to market
  * Cons: Lots of extension
* Rapid System Development and Evolution
* Ease of operation and Monitoring
  * Automation Around cluster detup, dashboard, alaert  
* Ease of User Onboarding and Debugging
  * Data Discovery
  * Data Audit
  * Self Service Onboarding 
   
