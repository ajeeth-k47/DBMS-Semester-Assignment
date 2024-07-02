# DBMS-Semester-Assignment
## Table of Contents
1. [Description](#description)
2. [Data Models](#data-models)
    - [MySQL Data Model](#mysql-data-model)
    - [MongoDB Single Collection Data Model](#mongodb-single-collection-data-model)
    - [MongoDB Two Collections Data Model](#mongodb-two-collections-data-model)
    - [Cassandra Data Model](#cassandra-data-model)
3. [MySQL Queries and Results](#mysql-queries-and-results)
4. [MongoDB Single Collection Queries and Results](#mongodb-single-collection-queries-and-results)
5. [MongoDB Two Collections Queries and Results](#mongodb-two-collections-queries-and-results)
6. [Cassandra Queries and Results](#cassandra-queries-and-results)

## Description
This project aims to determine the top product categories driving sales in an e-commerce environment and analyze how these preferences vary by customer demographics and age groups. To achieve this, we evaluate the performance and suitability of three different database systems: MySQL, MongoDB, and Cassandra.

### Approach
MySQL (Relational Database): Known for its robust support for complex queries and transactional integrity, MySQL provides a structured schema that is ideal for maintaining data consistency and enforcing relationships between different entities such as customers, orders, and products.

MongoDB (Document Database): With its flexible schema design, MongoDB allows for efficient querying by embedding related data together. This approach is particularly useful for handling varied data structures and evolving requirements without extensive schema redesign.

Cassandra (Column Database): Designed for high availability and scalability, Cassandra ensures fast read performance and efficiently distributes data to handle high volumes. Its schema is optimized for write-heavy operations, making it suitable for large-scale e-commerce applications.

By implementing these databases, we aim to compare their performance and identify which is most suitable for analyzing e-commerce sales data, focusing on the research question: What are the top product categories driving sales, and how do these preferences vary by customer demographics and age groups?

![MySQL_DataModel](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/b49dfb79-4f5a-49cb-891f-b547d51b2109)
