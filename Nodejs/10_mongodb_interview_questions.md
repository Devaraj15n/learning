#


### Mongodb:
- NOSQL document oriented database.
- that stores data in BSON documents.

unlike relational database, it doesnot require a fixed table schema.

### sql and NOsql



Sql | NOSQL
---- | ---- 
Relational Database | Non Relational database
table and Rows | document,key-value Pairs etc..
Pre-defined Schemas | Flexible Document structures 
SQL Queries | Database specific Query APIs
Supports relationship and Joins | Embedded documents or references


### What is a collection:
- group of documents in Mongodb, simular to tables in the database.


### What is document:
- Data record saved in the BSON format.


Example:
```json
{
    name:"deva",
    age:29,
    skills:[Nodejs,reactjs]
}

```
### Diff between find() and findOne():

find() - Matches and returns the all documents.
findOne() - Returns one matching document or null.


### Aggregation in Mongodb:

- Is a Process of handling the documents.
- Perform operations such as grouping,filtering,sorting and calculating totals.


#### $match - filter.


```javascript
db.orders.aggregare([
    {
        $match:{
                status:completed
            }
     }
    
]);

```

#### $sort - Sorting.

db.orders.aggregate([
    {
        $sort:{
            amount:-1
        }
    }
])

-1 is descending
1 is ascending


#### $group - Grouping (calculate total sales)
```javascript
db.orders.aggregate([
    {
        $group:{
            _id:null,
            totalSales:{
                $sum:"$amount"
            }
        }
    }
])
```
#### $sum - total sum.

### $project - select fields
```javascript
db.orders.aggregate([
    {
        $project:{
            customer_id:1,
            amount:1,
            _id:0
        }
    }
])
```


returns only customer_id,amount and exclude id


### What is Indexing in Mongodb:
- Indexing improves query performance to find matched documents efficiently.

db.users.createIndex({
    email:1
})


### What is Mongoose:
- IS an ODM(Object Data Modeling) which is used in Mongodb and Nodejs


It provides:

- schema.
- Middleware.
- Query Helpers.
- Validation.
- Models

