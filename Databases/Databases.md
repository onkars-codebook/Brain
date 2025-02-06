[[MongoDB]]
[[SqL]]
### Database Management Systems : 

 ### What is the Relational Database Management Systems ?
- `The RDBMS also stands for the Relational Database Mangement System in which data is stored in the form of row and columns like in the table format.`



### What is an Index in DBMS ?

An **index** in a Database Management System (DBMS) is a data structure that improves the speed of data retrieval operations on a database table. It works like an index in a book, allowing the database to find rows quickly without scanning the entire table.

1. **Primary Index**: Created on a primary key column; automatically unique.

2. **Secondary Index**: Created on non-primary key columns for faster searches.

3. **Clustered Index**: Determines the physical order of rows in a table. Only one per table.

4. **Non-Clustered Index**: Stores a reference (pointer) to the actual data, allowing multiple indexes per table.

5. **Unique Index**: Ensures uniqueness of values in the indexed column.

## Types of Indexing : 

- **Single-Level Indexing**
    - **Dense Index**: Every record has an entry in the index table.
    - **Sparse Index**: Only a few records have an entry, reducing index size but requiring more lookups.
- **Multi-Level Indexing**
    - A hierarchical structure where the first level contains pointers to the second level, making searches faster `(similar to a B-Tree)`.
- **B-Tree and B+ Tree Indexing**
    - Used in modern databases to maintain balanced search trees, reducing access time.
    - **B+ Tree** is commonly used as it keeps all data in leaf nodes, making sequential access efficient.
- **Hash Indexing**
    - Uses a **hash function** to map keys to specific memory locations, providing **O(1) search time** in ideal cases.



### **1. Understanding Query Optimization**

Query optimization is the process of improving the performance of a query by minimizing resource consumption such as CPU time, memory, and disk I/O.

### **2. Query Optimization Techniques**

#### **a) Indexing**

- Use **indexes** on frequently searched columns to speed up retrieval.
- Prefer **B-Tree or B+ Tree indexes** for range queries.
- Use **Hash indexes** for exact match queries.

#### **b) Avoiding Full Table Scans**

- Use **WHERE** conditions to filter data early.
- Avoid `SELECT *`; specify only required columns.

#### **c) Using Joins Efficiently**

- Prefer **INNER JOIN** over `WHERE` conditions for better optimization.
- Use **HASH JOIN** for large datasets and **NESTED LOOP JOIN** for small ones.
- Ensure **indexed columns** are used in join conditions.

#### **d) Optimizing Subqueries**

- Replace correlated subqueries with **JOINs** for better performance.
- Use **EXISTS** instead of `IN` for better execution.

#### **e) Partitioning Data**

- Implement **horizontal partitioning** to divide large tables into smaller subsets.
- Use **vertical partitioning** to store frequently accessed columns separately.

#### **f) Using Proper Data Types**

- Choose **integer** keys instead of **string-based** keys.
- Use **fixed-length data types** where possible.

#### **g) Query Execution Plan Analysis**

- Use `EXPLAIN` or `EXPLAIN ANALYZE` to examine query execution steps.
- Identify inefficient **scans**, **joins**, and **sort operations**.

#### **h) Caching and Materialized Views**

- Store **precomputed query results** to reduce computation time.
- Use **database caching mechanisms** like Redis for frequently accessed queries.

#### **i) Avoiding Unnecessary Sorting and Grouping**

- Use **indexed columns** in `ORDER BY` and `GROUP BY` operations.
- Avoid unnecessary sorting if the required order is already maintained by an index.

### **3. Query Optimization Tools**

- **MySQL EXPLAIN PLAN**
- **PostgreSQL Query Planner**
- **SQL Server Query Execution Plan**
- **Oracle SQL Trace & TKPROF**

### **4. Best Practices**

- Regularly analyze and optimize queries.
- Periodically rebuild indexes and update statistics.
- Use database profiling tools to identify slow queries.
