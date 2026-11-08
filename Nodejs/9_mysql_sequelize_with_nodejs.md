#



### how to connect Mysql with nodejs:

- connect using the `mysql2`.

```javascript

const mysql=require('mysql2');


const connection=mysql.createConnection({
  host:'localhost',
  user:"root",
  password:"",
  database:"test"
});


connection.connect((err)=>{
  if(err){
    console.log("Connection is not connected")
    return err;
  }

  console.log("Connection is established");
});
```


### Connection Pooling:

- maintains a resuable collection of database connections.
- Instead of creating new creation use the already existing connection.



```javascript


const mysql=require("mysql2/promise");

const pool = mysql.createPool({
  host:"local",
  user:"root",
  password:"",
  database:"test",
  connectionLimit:10

});


const [rows]=await pool.query("Select * from user where email =?",[1]);

```


### what is Sequelize:
- Sequelize is an ORM(Object relational Mapping) used in Nodejs.
- Allows developers to interact with the relational database using javascript objects and methods instead of writing sql query.


Support database include:
1.Mysql
2.Mariadb.
3.Microsoft Sql Server.
4.Postgresql.
5.SQLLite.


### ORM:
- Stands for Object Relational Mapping.
- It maps database tables to application Models and records to Objects.


```javascript
User.findAll({
    where:{
        email:"devaraj15.n@outlook.com"
    }
});

```

### diff between findOne() and findAll():
- findOne():
    - retrieves one matching record.
    - it returns Object or null.
    - `null` when record is empty.

- findAll();
    - retrieves matching all records.
    - it returns array.
    - if empty record, it is returned `[]`.


findOne() → One record → Object.

findAll() → All records → Array.

### What are sequelize associations:

- Defines the Relationships between models.


1. One to One (hasOne):
- Table A is connected to single record of Table B.

Users:

id Name
1  Deva
2  siddhu


user Profile:

id user_id city
1  1  chennai
2  2   Erode


```sql

User.hasOne(Profile,{
    foreignKey:'user_id'
});

Profile.belongsTo(User,{
    foreignKey:'user_id'
});

```

2. One to Many(hasMany):
- table A is connected to multipe records in table B.

Users:

id Name
1  Deva
2  Siddhu


Orders:
id user_id order
1   1     100
2   1     101
3   2     102


```sql
User.hasMany(Orders,{
    foreignKey:'user_id'
});

Orders.belongsTo(User,{
    foreignKey:'user_id'
});
```

3. Many to Many(belongstoMany):

- table A has multiple records and table B also has multiple records.
```sql
Student.hasMany(Course,{
    throgh:"StudentCourses",
    foreignKey:"student_id"
});


Course.belongsToMany("Student",{
    through:"StudentCourses",
    foreignKey:"course_id"
});
```


`StudentCourses` is the junction table.

student_id course_id
1            101
1            102
2            101



4. Belongs-To(belongsTo):
- this defines belongs to another model.

User.belongsTo(User,{
    foreignKey:"user_id"
});



### Eager Loading in Sequelize:

- Eager loading is a technique used to retrieve associated data along with the main data in a single query.

```sql

const users=User.findall({
    include:[
        {
            model:Order
        }
    ]
})

```


### database transactions:

- Group of Database Operations that should success or fail together.

ACID Principles:

1. Atomicity:
    - All Operation success or none success.
2. Consistency:
    - the database is still remain same before and after transaction.
3. Isolation:
    - doesnot interfere with other transactions.
4. Durability:
    - Once the changes are successfully committed, it changes are permantely saved, even if the application restarts.

```javascript
const transaction = new sequelie.transaction();


try{
    await Account.update(
        {balance:200},
        {
            where:{
                client_id:1
            },
            transaction
        }
    )
    await User.update(
        {balance:400},
        {
            where:{
                client_id:2
            },
            transaction
        }
    )
    transaction.commit();
}catch(error){
    transaction.rollback();
    throw error;
}

```

### SQL injection:

- Sql injection is malicious sql attack which is inserted in Database query.
- Use parameterized or ORM Methods.

```javascript
const query=`select * from users where email='${email}'`;
```

```javascript
const [rows]=await pool.execute('select * from users where email= ?',[email]);
```

### N+1 Query problem:
- One query fethes the list and another query which get the associated data.

Other solution:
1. Eager Loading.
2. Join.
3. Batching.
4. Dataloader


100 user -> 101 queries


Total Queries = 1 + N;


### How to improve the database Query Performance:
- Add Indexing.
- Pagination.
- Avoid (N+1) Queries.
- Optimize Joins.
- Use Connection pooling.
- Use caching where Appropriate.

