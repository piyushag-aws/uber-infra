## Real Time Use Cases @Uber
* Analytical Application - eg: Surge Pricing
* Dashboards: UberEats Restuarants Manager
* Machine Learning: Real time prediction monitoring
* Ad-hoc Exploration: ops automation

## Scalability Challenges
* Scaling Data: Expotential growth in terms PetaBytes  of Data
* Scaling Use Cases: New use cases from different business verticals. Eg: Dynamic Pricing
* Scaling Users: Large user base like engineers, data scientist, PM etc.

## Technical Requirements
1. Consistency - Avoid zero data lass with cross-regions and within region.
1. Availability - 99.99% availability goal for RTI
1. Data Freshness - Data should be eventual consistent within seconds
1. Query Latency - For some use case p99 to be in milliseconds
1. Scalability 
1. Cost - Reduce cost as much as possible while maintaining above requirements always.
1. Flexibility - Flexibility in terms of interface use. Like Programmatic vs SQL query.

## Layered Abstractions 
* [Lowest Layer] Storage: Blog Storage Interface, Read After Write Consistency(HDFS)
* Stream: Pub-sub interface (Apache Kafa)
* Compute: Works with Storage and Stream processing (Apache Flink)
* OLAP: Provides limited SQL capability over data coming from stream or storage. (Apache Pinot)
* SQL: Can work with both compute and OLAP. Full SQL query layer. (Presto)
* Programming API: For advanced users
* Metadata: Provides a simple interface to manage all kinds of metadata.

## Apache Kafka For Streaming Data
### Use Cases for Uber
* Pub/Sub
* Stream Processing
* Change Data Capture
* Ingestion into Data Lake
* Logging

### Cluster Federation
* Simple Discovery
* Scale Horizontally
* Tolerate single-cluster failure

### Dead Letter Queue(DLQ)
* Non-blocking and lossless events processing

### Consumer Proxy
* Proxy Layer in the middle
* Enhancment Over Kafka Protocol
* Take complexity away from receiver services
* Centralize management

## Apache Flink for Stream Processing
* Known for high-throughput, low-latency and fault-tolerant
* Fink as a Service(FaaS)
* FlinkSQL

## Apache Flink @Uber - Unified Platform
* Heterogeneous Systems
  * Job Type(SQL, FaaS, DSL)
  * Flink Version
  * Cluster Management System
* High Availability
  * Deployment Flow
  * Dependent Systems
* Deployment Efficiency
  * Minimum Donwtime during upgrade
  * Disaster Recovery
  * Relaibility of Ecosystem

## Apache Pinot
* Distributed, columan database
* Use cases at Uber
  * User-Facing Analystic


## Apache Pinot - Upserts
* First real-time OLAP to support upsert
* Challenge: Data Stored as immutable segments
* Data Partioning to share nothing


## Apache Pinot
* Full SQL Support 

## All Active Strategy
### Active-Active
* Replication in cross using uReplicator
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


## Things to Improve or Drawbacks to consider
### Use Completely Open Source vs some Dependencies on any Cloud providers(Hybrid Model)
* **HDFS(Hadoop Distributed File System) vs Cloud Storage(S3)**
  * Scalability: S3 is more scalable than HDFS.
  * Durability: When it comes to durability, S3 has the edge over HDFS.
  * Persistence: Data in S3 is always persistent, unlike data in HDFS. we need to do extra work in managing that.
  * Price: S3 is more cost-efficient and likely cheaper than HDFS.
*  **Manging Apache Kafka using some cloud providers like AWS vs Fully Managed Apache Kafka(DIY)**
  * **Pros**
    * Avoid engineering cost for mangement and re-invent the whole wheel.
    * More secure and adopt best pratices by default.
    * High availability and realiability.
  * **Cons**
    * There would be recurring cost for building custom data infrastructure. But this can be reduced with more optimized computer power as per the use cases.
* **SQL vs No-SQL**
* **Hybrid vs Self Managed Solution(DIY)**
* **No information mentioned in papaer about on premsis computation**
 *  Few simple ML models can be deployed on premsis.
 *  Avoid queries always to cloud for dashboard metrics 
* Caching layer looks to be missing.


   
