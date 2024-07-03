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

#### 3. Query to fetch category for which the customer spend lot of money
```
db.shopping_cart.aggregate([
  { $match: { customer_id: 1005 } },
  { $unwind: "$orders" },
  { $unwind: "$orders.sales" },
  { $lookup: { 
      from: "products", 
      localField: "orders.sales.product_id", 
      foreignField: "product_id", 
      as: "product_info"
    } 
  },
  { $unwind: "$product_info" },
  {  $group: {  _id: { category: "$product_info.category" }, 
      Total_Purchase_Price_For_EachCategory: { $sum: "$orders.sales.total_price" }, 
      customer_info: {  
        $first: {  first_name: "$first_name",  last_name: "$last_name",  gender: "$gender",  home_address: "$home_address"  }  } 
    }  },
  { $sort: { Total_Purchase_Price_For_EachCategory: -1 } },
  { $limit: 1 },
  {  $project: { 
      _id: 0, 
      first_name: "$customer_info.first_name", 
      last_name: "$customer_info.last_name", 
      gender: "$customer_info.gender", 
      home_address: "$customer_info.home_address", 
      category: "$_id.category", 
      Total_Purchase_Price_For_EachCategory: 1 } }
])
```
Time => ![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/87c2a9c7-44ca-4657-8e27-ad88118e1d94)
Result:
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/9d085710-a84d-4971-81ce-87b5a8ecca19)

#### 4. Query to fetch the total amount of quantity purchased per category by all customers in a state
```
db.customers.aggregate([
  { $unwind: "$orders" },
  { $unwind: "$orders.sales" },
  { $lookup: {
      from: "products",
      localField: "orders.sales.product_id",
      foreignField: "product_id",
      as: "product_info"
    }
  },
  { $unwind: "$product_info" },
  { $group: {
      _id: { state: "$state", category: "$product_info.category" },
      Total_Quantity: { $sum: "$orders.sales.quantity" },
      CountOfEachCategory_inEachState: { $sum: 1 }
    }
  },
  { $sort: {
      "_id.state": 1,
      Total_Quantity: -1
    }
  },
  { $group: {
      _id: "$_id.state",
      categories: {
        $push: {
          category: "$_id.category",
          Total_Quantity: "$Total_Quantity"
        }
      }
    }
  },
  { $project: {
      _id: 0,
      state: "$_id",
      top_category: { $arrayElemAt: ["$categories", 0] }
    }
  },
  { $unwind: "$top_category" },
  { $project: {
      state: 1,
      category_name: "$top_category.category",
      Total_Quantity: "$top_category.Total_Quantity"
    }
  },
  { $sort: {
      state: 1
    }
  }
])
```
Time => It tooks around 20 seconds to fetch the result.I cannot include the result because it take too much space here.


#### 5. Query to fetch no of quantity purchased by age group for each category
```
db.customers.aggregate([
  { $unwind: "$orders" },
  { $unwind: "$orders.sales" },
  { 
    $lookup: { 
      from: "products", 
      localField: "orders.sales.product_id", 
      foreignField: "product_id", 
      as: "product_info" 
    } 
  },
  { $unwind: "$product_info" },
  { 
    $lookup: { 
      from: "category", 
      localField: "product_info.category_id", 
      foreignField: "category_id", 
      as: "category_info" 
    } 
  },
  { $unwind: "$category_info" },
  { 
    $group: { 
      _id: { age: "$age", category_name: "$category_info.category_name" }, 
      Total_Quantity: { $sum: "$orders.sales.quantity" }, 
      Count_of_each_category_ineachage: { $sum: 1 }
    } 
  },
  { 
    $sort: { 
      "_id.age": 1, 
      Total_Quantity: -1 
    } 
  },
  { 
    $project: { 
      _id: 0, 
      age: "$_id.age", 
      category_name: "$_id.category_name", 
      Total_Quantity: 1, 
      Count_of_each_category_ineachage: 1 
    } 
  }
])
```
Time => it tooks around 32 seconds to fetch the result. I cannot include the result because it take too much space here.


### Cassandra Queries and Results
#### 1. Query to fetch frequently purchased category by a customer
```
CREATE TABLE my_keyspace.customer_category_aggregates (
customer_id int,
first_name text,
last_name text,
gender text,
home_address text,
category_id int,
category_name text,
total_purchase_price decimal,
PRIMARY KEY (customer_id, total_purchase_price, category_id)
) WITH CLUSTERING ORDER BY (total_purchase_price DESC);

SELECT 
first_name,
last_name,
gender,
home_address,
category_name,
category_id,
total_purchase_price
FROM my_keyspace.customer_category_aggregates
WHERE customer_id = 19
LIMIT 1;

```
or 
```
start_time = time.time()
def main():
    cluster = Cluster(['172.17.0.2'])
    session = cluster.connect('my_keyspace')
    query = "SELECT first_name, last_name, home_address, category_name, category_id FROM denormalized_data WHERE customer_id = 1005"
    rows = session.execute(query)
    counter = Counter((row.first_name, row.last_name, row.home_address, row.category_name, row.category_id) for row in rows)
    most_common_category = counter.most_common(1)
    if most_common_category:
        first_name, last_name, home_address, category_name, category_id = most_common_category[0][0]
        no_of_time_purchased = most_common_category[0][1]
        print(f"First Name: {first_name}, Last Name: {last_name}, Home address: {home_address}, Category Name: {category_name}, Category ID: {category_id}, No of Times Purchased: {no_of_time_purchased}")
    else:
        print("No purchases found for the customer.")
    cluster.shutdown()
if __name__ == "__main__":
    main()

end_time = time.time()
```

Time and Result:
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/d5e10c06-b8ff-42b9-acba-a21e8b29bfe7)

#### 2. Query to fetch the category with highest quantity that is purchased by a customer
```
start_time = time.time()
def main():
    cluster = Cluster(['172.17.0.2'])
    session = cluster.connect('my_keyspace')
    query = """
        SELECT first_name, last_name, home_address, category_name, category_id, quantity 
        FROM denormalized_data 
        WHERE customer_id = 1005
    """
    rows = session.execute(query)
    category_totals = defaultdict(int)
    customer_info = None
    for row in rows:
        if not customer_info:
            customer_info = {
                'first_name': row.first_name,
                'last_name': row.last_name,
                'home_address': row.home_address
            }
        category_name = row.category_name
        category_id = row.category_id
        quantity = row.quantity
        category_totals[(category_name, category_id)] += quantity
    sorted_categories = sorted(category_totals.items(), key=lambda x: x[1], reverse=True)
    if customer_info:
        print(f"Customer Information:")
        print(f"   - First Name: {customer_info['first_name']}")
        print(f"   - Last Name: {customer_info['last_name']}")
        print(f"   - Home Address: {customer_info['home_address']}")
    else:
        print("No customer information found.")
    if sorted_categories:
        print("\nCategories Purchased:")
        for (category_name, category_id), total_quantity in sorted_categories:
            print(f"   - Category Name: {category_name}, Category ID: {category_id}, Total Quantity Purchased: {total_quantity}")
    else:
        print("No purchases found for the customer.")
    cluster.shutdown()

if __name__ == "__main__":
    main()

end_time = time.time()
```

Time and Result: 
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/0233fcc4-e338-492d-911a-05c35493064b)

#### 3. Query to fetch category for which the customer spend lot of money

```

CREATE TABLE my_keyspace.customer_category_aggregates_s3 (
customer_id int,
first_name text,
last_name text,
gender text,
home_address text,
category_id int,
category_name text,
total_purchase_price decimal,
PRIMARY KEY (customer_id, total_purchase_price, category_id)
) WITH CLUSTERING ORDER BY (total_purchase_price DESC);

SELECT 
first_name,
last_name,
gender,
home_address,
category_name,
category_id,
total_purchase_price
FROM my_keyspace.customer_category_aggregates_s3
WHERE customer_id = 19
LIMIT 1;

```

or

```
start_time = time.time()
def main():
    cluster = Cluster(['172.17.0.2'])
    session = cluster.connect('my_keyspace')

    query = """
        SELECT first_name, last_name, gender, home_address, category_name, category_id, total_price
        FROM denormalized_data
        WHERE customer_id = 1005
    """
    rows = session.execute(query)
    category_totals = defaultdict(int)
    customer_info = None

    for row in rows:
        if not customer_info:
            customer_info = {
                'first_name': row.first_name,
                'last_name': row.last_name,
                'gender': row.gender,
                'home_address': row.home_address
            }

        category_name = row.category_name
        category_id = row.category_id
        total_price = row.total_price
        category_totals[(category_name, category_id)] += total_price

    if category_totals:
        most_purchased_category = max(category_totals, key=category_totals.get)
        category_name, category_id = most_purchased_category
        total_purchase_price = category_totals[most_purchased_category]

        print statement...
 
    else:
        print("No purchases found for the customer.")

    cluster.shutdown()

if __name__ == "__main__":
    main()

end_time = time.time()
```
Time and Results:
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/b4cedb7a-20a5-4747-9164-669fe9c04a70)


#### 4. Query to fetch the total amount of quantity purchased per category by all customers in a state
```
start_time = time.time()
def main():
    cluster = Cluster(['172.17.0.2'])
    session = cluster.connect('my_keyspace')
    query = """
    SELECT state, category_name, quantity
    FROM denormalized_data
    """
    rows = session.execute(query)
    state_category_stats = defaultdict(lambda: defaultdict(int))
    for row in rows:
        state = row.state
        category_name = row.category_name
        quantity = row.quantity
        state_category_stats[state][category_name] += quantity
    for state, categories in state_category_stats.items():
        print(f"State: {state}")
        for category_name, total_quantity in categories.items():
            print(f"   Category Name: {category_name}, Total Quantity: {total_quantity}")
    cluster.shutdown()
if __name__ == "__main__":
    main()
end_time = time.time()
```

Time and Results: 
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/ee5572c8-2dea-4b31-b842-224ac375bdd9)

#### 5. Query to fetch no of quantity purchased by age group for each category
```
start_time = time.time()
def connect_to_cassandra():
    try:
        cluster = Cluster(['172.17.0.2'])
        session = cluster.connect('my_keyspace')
        return cluster, session
    except Exception as e:
        print(f"Error connecting to Cassandra: {str(e)}")
        return None, None
def fetch_data(session):
    try:
        query = """
        SELECT age, category_name, quantity
        FROM denormalized_data
        """
        rows = session.execute(query)
        return rows
    except Exception as e:
        print(f"Error executing query: {str(e)}")
        return None
def process_data(rows):
    try:
        age_group_category_stats = defaultdict(lambda: defaultdict(int))
        for row in rows:
            age = row.age
            category_name = row.category_name
            quantity = row.quantity
            if 20 <= age <= 29:
                age_group = '20-29'
            elif 30 <= age <= 39:
                age_group = '30-39'
            elif 40 <= age <= 49:
                age_group = '40-49'
            elif 50 <= age <= 59:
                age_group = '50-59'
            elif 60 <= age <= 69:
                age_group = '60-69'
            elif 70 <= age <= 79:
                age_group = '70-79'
            else:
                age_group = 'Other'
            age_group_category_stats[age_group][category_name] += quantity
        return age_group_category_stats
    except Exception as e:
        print(f"Error processing data: {str(e)}")
        return None
def print_stats(age_group_category_stats):
    try:
        for age_group, categories in age_group_category_stats.items():
            print(f"Age Group: {age_group}")
            for category_name, total_quantity in categories.items():
                print(f"    Category Name: {category_name}, Total Quantity: {total_quantity}")
            print()
    except Exception as e:
        print(f"Error printing statistics: {str(e)}")
def close_connection(cluster):
    try:
        if cluster:
            cluster.shutdown()
    except Exception as e:
        print(f"Error closing connection: {str(e)}")
def main():
    cluster, session = connect_to_cassandra()
    if not session:
        return
    rows = fetch_data(session)
    if not rows:
        close_connection(cluster)
        return
    age_group_category_stats = process_data(rows)
    if not age_group_category_stats:
        close_connection(cluster)
        return
    print("Age Group Category Statistics:")
    print_stats(age_group_category_stats)
    close_connection(cluster)
if __name__ == "__main__":
    main()
end_time = time.time()
```
Time and Results: 
![image](https://github.com/ajeeth-k47/DBMS-Semester-Assignment/assets/66105938/d0ee28d0-69fe-43d4-8783-0bbac8372afc)







