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

Time => 1 row retrieved starting from 1 in 96 ms (execution: 19 ms, fetching: 77 ms)

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

Time  => 3 rows retrieved starting from 1 in 107 ms (execution: 25 ms, fetching: 82 ms)

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

Time  =>  1 row retrieved starting from 1 in 111 ms (execution: 11 ms, fetching: 100 ms)

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
Time => 174 rows retrieved starting from 1 in 851 ms (execution: 822 ms, fetching: 29 ms)

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
Time => 189 rows retrieved starting from 1 in 813 ms (execution: 783 ms, fetching: 30 ms)

### MongoDB Single Collection Queries and Results
#### 1. Query to fetch frequently purchased category by a customer
```
db.customers.aggregate([
  {$match: {customer_id: 1005}},
  {$unwind: "$orders"},
  {$unwind: "$orders.sales"},
  {$group: {
    _id: {
      category_name: "$orders.sales.product.category_name",
      first_name: "$first_name",
      last_name: "$last_name",
      home_address: "$home_address"
    },
    No_of_time_purchased: {$sum: 1}
  }},
  {$project: {
    _id: 0,
    first_name: "$_id.first_name",
    last_name: "$_id.last_name",
    home_address: "$_id.home_address",
    category_name: "$_id.category_name",
    No_of_time_purchased: 1
  }},
  {$sort: {No_of_time_purchased: -1}},
  {$limit: 1}
]);
```
Time => ![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/f8216c5d-49ef-4dad-be7d-32de4c5e6fb9)

Result:  
```
{
  "No_of_time_purchased": 5,
  "first_name": "Imran",
  "last_name": "Pai",
  "home_address": "002 Beau PlazaApt. 308",
  "category_name": "Shirt"
}
```
#### 2. Query to fetch the category with highest quantity that is purchased by a customer
```
db.collection.aggregate([
  {$match: {customer_id: 1005}},
  {$unwind: "$orders"},
  {$unwind: "$orders.sales"},
  {$group: {
    _id: {
      category_name: "$orders.sales.product.category_name",
      category_id: "$orders.sales.product.category_id"
    },
    No_of_quantity_purchased: {$sum: "$orders.sales.quantity"},
    first_name: {$first: "$first_name"},
    last_name: {$first: "$last_name"},
    home_address: {$first: "$home_address"}
  }},
  {$sort: {No_of_quantity_purchased: -1}}
]);
```
Time => ![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/7fff7595-89d3-49e2-817a-dedae131d48f)

Result: 
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/cad0af66-e759-4425-9910-64f1b33992bd)

#### 3. Query to fetch category for which the customer spend lot of money
```
db.collection.aggregate([
  {$match: {customer_id: 1005}},
  {$unwind: "$orders"},
  {$unwind: "$orders.sales"},
  {$group: {
    _id: {
      category_name: "$orders.sales.product.category_name",
      category_id: "$orders.sales.product.category_id"
    },
    Total_Purchase_Price_For_EachCategory: {$sum: "$orders.sales.total_price"},
    first_name: {$first: "$first_name"},
    last_name: {$first: "$last_name"},
    gender: {$first: "$gender"},
    home_address: {$first: "$home_address"}
  }},
  {$sort: {Total_Purchase_Price_For_EachCategory: -1}},
  {$limit: 1}
]);
```
Time => ![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/8cad06ce-7b7a-4d1e-846c-6a2973b7bb4b)

Result:
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/924dbfc2-a6fe-4d7d-a8e9-9b19defbabad)

#### 4. Query to fetch the total amount of quantity purchased per category by all customers in a state
```
db.collection.aggregate([
  {$unwind: "$orders"},
  {$unwind: "$orders.sales"},
  {$project: {
    state: "$state",
    category_name: "$orders.sales.product.category_name",
    quantity: "$orders.sales.quantity"
  }},
  {$group: {
    _id: {
      state: "$state",
      category_name: "$category_name"
    },
    Total_Quantity: {$sum: "$quantity"},
    CountOfEachCategory_inEachState: {$sum: 1}
  }},
  {$project: {
    _id: 0,
    state: "$_id.state",
    category_name: "$_id.category_name",
    Total_Quantity: 1,
    CountOfEachCategory_inEachState: 1
  }},
  {$sort: {state: 1, Total_Quantity: -1}}
]);
```
Time => ![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/b4f51dcf-ee8b-4723-a244-4d7edc398f89)

Result:
total 172 documents here I specified small amount of result as it consumes lot of space
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/fd481031-527f-43f5-a690-2a730010abc9)

#### 5. Query to fetch no of quantity purchased by age group for each category
```
db.customers.aggregate([
  {$unwind: "$orders"},
  {$unwind: "$orders.sales"},
  {$group: {
    _id: {
      age: "$age",
      category_name: "$orders.sales.product.category_name"
    },
    Total_Quantity: {$sum: "$orders.sales.quantity"},
    Count_of_each_category_in_each_age: {$sum: 1}
  }},
  {$project: {
    _id: 0,
    age: "$_id.age",
    category_name: "$_id.category_name",
    Total_Quantity: 1,
    Count_of_each_category_in_each_age: 1
  }},
  {$sort: {age: 1, Total_Quantity: -1}}
]);
```
Time => ![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/aa39940a-824c-4a39-b838-73682c6bf293)


#### MongoDB Two Collections Queries and Results

#### 1. Query to fetch frequently purchased category by a customer
```
db.customers.aggregate([
  {$match:{customer_id:1005}},
  {$unwind:"$orders"},
  {$unwind:"$orders.sales"},
  {$lookup:{
    from:"products",
    localField:"orders.sales.product_id",
    foreignField:"product_id",
    as:"product_info"
  }},
  {$unwind:"$product_info"},
  {$group:{
    _id:{
      category_name:"$product_info.category",
      category_id:"$product_info.category_id",
      first_name:"$first_name",
      last_name:"$last_name",
      home_address:"$home_address"
    },
    No_of_time_purchased:{$sum:1}
  }},
  {$project:{
    _id:0,
    first_name:"$_id.first_name",
    last_name:"$_id.last_name",
    home_address:"$_id.home_address",
    category_name:"$_id.category_name",
    category_id:"$_id.category_id",
    No_of_time_purchased:1
  }},
  {$sort:{No_of_time_purchased:-1}},
  {$limit:1}
]);
```
Time => ![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/41ac1dc8-7439-42db-9cee-f667ad199dab)

Results: 
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/e2018e44-3b99-4f93-89fe-a45bfeafe881)

#### 2. Query to fetch the category with highest quantity that is purchased by a customer
```
db.shopping_cart.aggregate([
  {$match:{customer_id:1005}},
  {$unwind:"$orders"},
  {$unwind:"$orders.sales"},
  {$lookup:{
    from:"products",
    localField:"orders.sales.product_id",
    foreignField:"product_id",
    as:"product_info"
  }},
  {$unwind:"$product_info"},
  {$group:{
    _id:{category:"$product_info.category"},
    No_of_quantity_purchased:{$sum:"$orders.sales.quantity"},
    customer_info:{$first:{first_name:"$first_name",last_name:"$last_name",home_address:"$home_address"}}
  }},
  {$sort:{No_of_quantity_purchased:-1}},
  {$project:{
    _id:0,
    first_name:"$customer_info.first_name",
    last_name:"$customer_info.last_name",
    home_address:"$customer_info.home_address",
    category:"$_id.category",
    No_of_quantity_purchased:1
  }}
]);
```
Time => ![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/55cec64d-9850-48f9-809c-f214f7aeea7d)

Result: 
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/c6091236-c1f9-4129-92b3-384c4a673086)

