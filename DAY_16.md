# **AWS Training - Day 14**

# Databases (RDBMS and No-SQL Databases)

## NoSQL databases
1. **Key-Value Stores**:  
   - These are the simplest type of NoSQL databases where data is stored as key-value pairs.  
   - Examples: **Redis**, **Amazon DynamoDB**.  
   - Best suited for caching and session management due to their high-performance retrieval.

2. **Document Stores**:  
   - These databases store data in a document-like format, usually JSON, BSON, or XML.  
   - Examples: **MongoDB**, **Couchbase**.  
   - Perfect for applications that handle complex, hierarchical data.

3. **Column-Oriented Databases**:  
   - Data is stored in columns instead of rows, optimized for analytical workloads and high scalability.  
   - Examples: **Apache Cassandra**, **HBase**.  
   - Often used in big data applications and distributed systems.

4. **Graph Databases**:  
   - Designed to store relationships between data as graphs (nodes, edges, properties).  
   - Examples: **Neo4j**, **Amazon Neptune**.  
   - Ideal for applications like social networks, fraud detection, or recommendation engines.

## CAP principle in NO-SQL
CAP stands for **Consistency, Availability, and Partition Tolerance**, which are three key aspects defined by the CAP theorem for distributed database systems. Here's what they mean:

1. **Consistency**: Ensures that every read from the database provides the most recent write or update. This means all nodes in the system see the same data at the same time.

2. **Availability**: Guarantees that every request receives a response—success or failure—even if some nodes in the system are down. The system remains operational.

3. **Partition Tolerance**: Deals with network failures or partitions. It ensures the system continues to operate correctly even if communication between nodes is interrupted.

The CAP theorem states that a distributed system can achieve at most two of these three properties at any given time—not all three simultaneously. This means you have to choose between consistency, availability, and partition tolerance depending on your application's requirements.



# Amazon RDS Overview

Aurora - serverless

RDS deployment

read-Replica -> availabulity of read operation
multi-AZ -> high availability
multi-Region ->


ElastiCache - in memory data storage fully managed

DynamoDB
    key/value and document

DynamoDB Accelerator - DAX

DynamoDB Global Table

Redshift

EMR (Elastic MapReduce) - Hadoop

Athena (data in s3 when need to analyze use athena)

QuickSite

DocumentDB

Neptune - graph db

Timestream

QLDB

Managed Blockchain

GLue