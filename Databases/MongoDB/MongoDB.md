[[Mongoose]]
[[Operations]]
# Introduction to MongoDB

MongoDB is a source-available, cross-platform, document-oriented database program. Classified as a NoSQL database, it utilizes JSON-like documents with optional schemas.

## Document Database

In MongoDB, records are stored as documents, which are data structures composed of field and value pairs. These documents are similar to JSON objects, and their values may include other documents, arrays, and arrays of documents. The advantages of using documents include:

- **Alignment with Native Data Types**: Documents correspond to native data types in many programming languages.
- **Reduced Need for Joins**: Embedded documents and arrays reduce the need for expensive joins.
- **Dynamic Schema**: Supports fluent polymorphism, allowing for flexible and dynamic data models.

## Collections, Views, and On-Demand Materialized Views

MongoDB stores documents in collections, which are analogous to tables in relational databases. In addition to collections, MongoDB supports:

- **Read-only Views**
- **On-Demand Materialized Views**

## Key Features

### High Performance

MongoDB provides high-performance data persistence through:

- **Embedded Data Models**: Support for embedded data models reduces I/O activity on the database system.
- **Indexes**: Support faster queries and can include keys from embedded documents and arrays.

### Query API

The MongoDB Query API supports read and write operations (CRUD) as well as:

- **Data Aggregation**
- **Text Search**
- **Geospatial Queries**

### High Availability

MongoDB's replication facility, called a replica set, provides:

- **Automatic Failover**
- **Data Redundancy**

A replica set is a group of MongoDB servers that maintain the same data set, providing redundancy and increasing data availability.

### Horizontal Scalability

MongoDB offers horizontal scalability as part of its core functionality:

- **Sharding**: Distributes data across a cluster of machines.
- **Zones**: Starting in version 3.4, MongoDB supports creating zones of data based on the shard key. In a balanced cluster, MongoDB directs reads and writes covered by a zone only to those shards inside the zone.

### Support for Multiple Storage Engines

MongoDB supports multiple storage engines:

- **WiredTiger Storage Engine**: Includes support for Encryption at Rest.
- **In-Memory Storage Engine**: For self-managed deployments.

Additionally, MongoDB provides a pluggable storage engine API that allows third parties to develop storage engines for MongoDB.

## Editions

MongoDB is available in several editions:

- **MongoDB Atlas**: The fully managed service for MongoDB deployments in the cloud.
- **MongoDB Enterprise**: The subscription-based, self-managed version of MongoDB.
- **MongoDB Community**: The source-available, free-to-use, and self-managed version of MongoDB.

## History

MongoDB was first released in February 2009 by 10gen (now MongoDB Inc.). It supports features like sharding, replication, and ACID transactions (from version 4.0). MongoDB Atlas, its managed cloud service, operates on AWS, Google Cloud Platform, and Microsoft Azure. Current versions are licensed under the Server Side Public License (SSPL). 
## Licensing

For more detailed information, refer to the [official MongoDB documentation](https://www.mongodb.com/docs/manual/introduction/).
