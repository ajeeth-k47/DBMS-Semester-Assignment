# DBMS-Semester-Assignment
## Table of Contents
1. [Description](#description)
2. [Data Models](#data-models)
    - [MySQL Data Model](#mysql-data-model)
    - [MongoDB Data Model With Single Collection](#mongodb-data-model-with-single-collection)
    - [MongoDB Data Model With Two Collections](#mongodb-data-model-with-two-collections)
    - [Cassandra Data Model](#cassandra-data-model)
3. [MySQL Queries and Results](#mysql-queries-and-results)
4. [MongoDB Single Collection Queries and Results](#mongodb-single-collection-queries-and-results)
5. [MongoDB Two Collections Queries and Results](#mongodb-two-collections-queries-and-results)
6. [Cassandra Queries and Results](#cassandra-queries-and-results)

## Description
This project aims to determine the top product categories driving sales in an e-commerce environment and analyze how these preferences vary by customer demographics and age groups. To achieve this, we evaluate the performance and suitability of three different database systems: MySQL, MongoDB, and Cassandra.

### Approach
- MySQL (Relational Database): Known for its robust support for complex queries and transactional integrity, MySQL provides a structured schema that is ideal for maintaining data consistency and enforcing relationships between different entities such as customers, orders, and products.

- MongoDB (Document Database): With its flexible schema design, MongoDB allows for efficient querying by embedding related data together. This approach is particularly useful for handling varied data structures and evolving requirements without extensive schema redesign.

- Cassandra (Column Database): Designed for high availability and scalability, Cassandra ensures fast read performance and efficiently distributes data to handle high volumes. Its schema is optimized for write-heavy operations, making it suitable for large-scale e-commerce applications.

By implementing these databases, we aim to compare their performance and identify which is most suitable for analyzing e-commerce sales data, focusing on the research question: What are the top product categories driving sales, and how do these preferences vary by customer demographics and age groups?

## Data Models

### MySQL Data Model
![MySQL_DataModel](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/b49dfb79-4f5a-49cb-891f-b547d51b2109)

### MongoDB Data Model With Single Collection
```json{
  $jsonSchema: {
    bsonType: "object",
    required: [
      "customer_id",
      "first_name",
      "last_name",
      "gender",
      "age",
      "home_address",
      "zip_code",
      "city",
      "state",
      "country",
      "orders"
    ],
    properties: {
      customer_id: {
        bsonType: "int",
        description:
          "must be an integer and is required"
      },
      first_name: {
        bsonType: "string",
        description:
          "must be a string and is required"
      },
      last_name: {
        bsonType: "string",
        description:
          "must be a string and is required"
      },
      gender: {
        bsonType: "string",
        description:
          "must be a string and is required"
      },
      age: {
        bsonType: "int",
        description:
          "must be an integer and is required"
      },
      home_address: {
        bsonType: "string",
        description:
          "must be a string and is required"
      },
      zip_code: {
        bsonType: "string",
        description:
          "must be a string and is required"
      },
      city: {
        bsonType: "string",
        description:
          "must be a string and is required"
      },
      state: {
        bsonType: "string",
        description:
          "must be a string and is required"
      },
      country: {
        bsonType: "string",
        description:
          "must be a string and is required"
      },
      orders: {
        bsonType: "array",
        items: {
          bsonType: "object",
          required: [
            "order_id",
            "order_date",
            "delivery_date",
            "sales"
          ],
          properties: {
            order_id: {
              bsonType: "int",
              description:
                "must be an integer and is required"
            },
            order_date: {
              bsonType: "date"
            },
            delivery_date: {
              bsonType: "date"
            },
            sales: {
              bsonType: "array",
              items: {
                bsonType: "object",
                required: [
                  "sales_id",
                  "price_per_unit",
                  "quantity",
                  "total_price",
                  "product"
                ],
                properties: {
                  sales_id: {
                    bsonType: "int",
                    description:
                      "must be an integer and is required"
                  },
                  price_per_unit: {
                    bsonType: "number",
                    description:
                      "must be a number and is required"
                  },
                  quantity: {
                    bsonType: "int",
                    description:
                      "must be an integer and is required"
                  },
                  total_price: {
                    bsonType: "number",
                    description:
                      "must be a number and is required"
                  },
                  product: {
                    bsonType: "object",
                    required: [
                      "product_id",
                      "product_name",
                      "size",
                      "colour",
                      "price",
                      "description",
                      "category_name"
                    ],
                    properties: {
                      product_id: {
                        bsonType: "int",
                        description:
                          "must be an integer and is required"
                      },
                      product_name: {
                        bsonType: "string",
                        description:
                          "must be a string and is required"
                      },
                      size: {
                        bsonType: "string",
                        description:
                          "must be a string and is required"
                      },
                      colour: {
                        bsonType: "string",
                        description:
                          "must be a string and is required"
                      },
                      price: {
                        bsonType: "number",
                        description:
                          "must be a number and is required"
                      },
                      description: {
                        bsonType: "string",
                        description:
                          "must be a string and is required"
                      },
                      category_name: {
                        bsonType: "string",
                        description:
                          "must be a string and is required"
                      }
                    }
                  }
                }
              }
            }
          }
        }
      }
    }
  }
}
```

### MongoDB Data Model With Two Collections
#### customers
```json
{
  "$jsonSchema": {
    "bsonType": "object",
    "required": [
      "first_name",
      "last_name",
      "gender",
      "age",
      "home_address",
      "zip_code",
      "city",
      "state",
      "country",
      "orders"
    ],
    "properties": {
      "first_name": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "last_name": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "gender": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "age": {
        "bsonType": "int",
        "description": "must be an integer and is required"
      },
      "home_address": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "zip_code": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "city": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "state": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "country": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "orders": {
        "bsonType": "array",
        "items": {
          "bsonType": "object",
          "required": [
            "order_date",
            "delivery_date",
            "sales"
          ],
          "properties": {
            "order_date": {
              "bsonType": "date",
              "description": "must be a date and is required"
            },
            "delivery_date": {
              "bsonType": "date",
              "description": "must be a date and is required"
            },
            "sales": {
              "bsonType": "array",
              "items": {
                "bsonType": "object",
                "required": [
                  "product_id",
                  "price_per_unit",
                  "quantity",
                  "total_price"
                ],
                "properties": {
                  "product_id": {
                    "bsonType": "int",
                    "description": "must be an integer and is required"
                  },
                  "price_per_unit": {
                    "bsonType": "number",
                    "description": "must be a number and is required"
                  },
                  "quantity": {
                    "bsonType": "int",
                    "description": "must be an integer and is required"
                  },
                  "total_price": {
                    "bsonType": "number",
                    "description": "must be a number and is required"
                  }
                }
              }
            }
          }
        }
      }
    }
  }
}

```
#### products
```json
{
  "$jsonSchema": {
    "bsonType": "object",
    "required": [
      "product_id",
      "product_name",
      "size",
      "colour",
      "price",
      "quantity",
      "description",
      "category"
    ],
    "properties": {
      "product_id": {
        "bsonType": "int",
        "description": "must be an integer and is required"
      },
      "product_name": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "size": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "colour": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "price": {
        "bsonType": "number",
        "description": "must be a number and is required"
      },
      "quantity": {
        "bsonType": "int",
        "description": "must be an integer and is required"
      },
      "description": {
        "bsonType": "string",
        "description": "must be a string and is required"
      },
      "category": {
        "bsonType": "string",
        "description": "must be string and is required"
      }
    }
  }
}
```

### Cassandra Data Model

![Cassandra_DataModel](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/39ce541d-2f0f-438e-ab52-87993923f566)

## MySQL Queries and Results

#### 1. Query to fetch frequently purchased category by a customer
```
               SELECT
                   customer.first_name,
                   customer.last_name,
                   customer.home_address,
                   category.category_name,
                   category.category_id,
                   count(*) as 'No_of_time_purchased'
               FROM customer
               INNER JOIN orders
               ON customer.customer_id = orders.customer_id
               INNER JOIN sales
               ON sales.order_id = orders.order_id
               INNER JOIN products
               ON sales.product_id = products.product_id
               INNER JOIN category
               ON products.category_id=category.category_id
               WHERE customer.customer_id=1005
               GROUP BY category.category_name, category.category_id
               order by  No_of_time_purchased desc LIMIT 1
```

Time => 1 row retrieved starting from 1 in 336 ms (execution: 315 ms, fetching: 21 ms)

Result:
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/47db066a-6116-4770-8438-5c643ef7730b)

#### 2. Query to fetch the category with highest quantity that is purchased by a customer
```
SELECT
    customer.first_name,
    customer.last_name,
    customer.home_address,
    category.category_name,
    category.category_id,
    SUM(sales.quantity) as 'No_of_quantity_purchased'
FROM customer
INNER JOIN orders
ON customer.customer_id = orders.customer_id
INNER JOIN sales
ON sales.order_id = orders.order_id
INNER JOIN products
ON sales.product_id = products.product_id
INNER JOIN category
ON products.category_id=category.category_id
WHERE customer.customer_id=1005
GROUP BY category.category_name, category.category_id
order by  No_of_quantity_purchased desc;
```
Time => 3 rows retrieved starting from 1 in 291 ms (execution: 262 ms, fetching: 29 ms)

Result: 
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/f27367d1-f773-4f7d-a48c-d20416ca79a1)

#### 3. Query to fetch category for which the customer spend lot of money
```
SELECT
    customer.first_name,
    customer.last_name,
    customer.gender,
    customer.home_address,
    category.category_name,
    category.category_id,
    SUM(sales.total_price) as 'Total_Purchase_Price_For_EachCategory'
FROM customer
INNER JOIN orders
ON customer.customer_id = orders.customer_id
INNER JOIN sales
ON sales.order_id = orders.order_id
INNER JOIN products
ON sales.product_id = products.product_id
INNER JOIN category
ON products.category_id=category.category_id
WHERE customer.customer_id=1005
GROUP BY category.category_name, category.category_id
ORDER BY Total_Purchase_Price_For_EachCategory DESC LIMIT 1;
```
Time => 1 row retrieved starting from 1 in 340 ms (execution: 321 ms, fetching: 19 ms)

Result:
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/f0991578-392a-4627-8051-a91ec37fa163)


#### 4. Query to fetch the total amount of quantity purchased per category by all customers in a state
```
SELECT
    customer.state,
    category.category_name,
    SUM(sales.quantity) as "Total_Quantity",
    COUNT(*) as "CountOfEachCategory_inEachState"
FROM customer
INNER JOIN orders
ON customer.customer_id = orders.customer_id
INNER JOIN sales
ON sales.order_id = orders.order_id
INNER JOIN products
ON sales.product_id = products.product_id
INNER JOIN category
ON products.category_id=category.category_id
GROUP BY category.category_name, customer.state
ORDER BY customer.state ASC,Total_Quantity DESC;
```
Time => 174 rows retrieved starting from 1 in 746 ms (execution: 722 ms, fetching: 24 ms)

#### 5. Query to fetch no of quantity purchased by age group for each category
```
SELECT
    customer.age,
    category.category_name,
    SUM(sales.quantity) as "Total_Quantity",
    COUNT(*) as "Count_of_each_category_ineachage"
FROM customer
INNER JOIN orders
ON customer.customer_id = orders.customer_id
INNER JOIN sales
ON sales.order_id = orders.order_id
INNER JOIN products
ON sales.product_id = products.product_id
INNER JOIN category
ON products.category_id=category.category_id
GROUP BY category.category_name, customer.age
ORDER BY customer.age ASC,Total_Quantity DESC;
```
Time => 189 rows retrieved starting from 1 in 727 ms (execution: 675 ms, fetching: 52 ms)
