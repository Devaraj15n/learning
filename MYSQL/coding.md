```sql

-- create
CREATE TABLE Customer (
    CustomerId INTEGER PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL
);

CREATE TABLE Orders (
    OrderId INTEGER PRIMARY KEY,
    CustomerId INTEGER NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (CustomerId) REFERENCES Customer(CustomerId)
);
-- insert
INSERT INTO Customer VALUES (0001, 'Clark', 'deva@gmail');
INSERT INTO Customer VALUES (0002, 'Dave', 'deva1@gmail');
INSERT INTO Customer VALUES (0003, 'Ava', 'deva2@gmail');
INSERT INTO Customer VALUES (0004, 'Vibin', 'vibib@gmail');



-- insert
INSERT INTO Orders VALUES (0001, 0001, 50000);
INSERT INTO Orders VALUES (0002, 0002, 20000);
INSERT INTO Orders VALUES (0003, 0003, 10000);




-- get all customers and their amount
select c.name,o.amount from Customer c
inner join Orders o on o.CustomerId=c.CustomerId;

+-------+----------+
| name  | amount   |
+-------+----------+
| Clark | 50000.00 |
| Dave  | 20000.00 |
| Ava   | 10000.00 |
+-------+----------+


-- get customers who have not placed any orders;

select c.name,c.email from Customer c
left join Orders o on o.CustomerId=c.CustomerId
where o.OrderId is NULL;


+-------+-------------+
| name  | email       |
+-------+-------------+
| Vibin | vibib@gmail |
+-------+-------------+


-- get customer whose order is greater than 20000

select c.name,c.email,o.amount from Customer c
inner join Orders o on o.CustomerId=c.CustomerId
where o.amount > 20000;

+-------+------------+----------+
| name  | email      | amount   |
+-------+------------+----------+
| Clark | deva@gmail | 50000.00 |
+-------+------------+----------+

-- get all customers,including customers who haven't including orders

select c.name,o.amount from Customer c
left join Orders o on o.CustomerId=c.CustomerId;

+-------+----------+
| name  | amount   |
+-------+----------+
| Clark | 50000.00 |
| Dave  | 20000.00 |
| Ava   | 10000.00 |
| Vibin |     NULL |
+-------+----------+


-- get total number of orders
select count(*) as total_orders from Orders;


+--------------+
| total_orders |
+--------------+
|            3 |
+--------------+

INSERT INTO Orders VALUES (0004, 0001, 40000);

-- Group By

-- get total order with each customer amount

select c.name,SUM(o.amount) as total_amount from Customer c
inner join Orders o on o.CustomerId=c.CustomerId
group by c.CustomerId,c.name;

+-------+--------------+
| name  | total_amount |
+-------+--------------+
| Clark |     90000.00 |
| Dave  |     20000.00 |
| Ava   |     10000.00 |
+-------+--------------+


-- find customer whose total amount is greater than 20000

select c.name,SUM(o.amount) as total_amount from Customer c
inner join Orders o on o.CustomerId=c.CustomerId
group by c.CustomerId,c.name
having SUM(o.amount) > 20000;

+-------+--------------+
| name  | total_amount |
+-------+--------------+
| Clark |     90000.00 |
+-------+--------------+

-- find the highest order amount.

select Max(amount) from Orders;

+-------------+
| Max(amount) |
+-------------+
|    50000.00 |
+-------------+


-- find the average amount

select AVG(amount) from Orders;

+--------------+
| AVG(amount)  |
+--------------+
| 30000.000000 |
+--------------+


-- find the number of orders count by the customers

select c.CustomerId,count(o.OrderId) as total_orders from Customer c
left join Orders o on o.CustomerId=c.CustomerId
group by c.CustomerId,c.name;

+------------+--------------+
| CustomerId | total_orders |
+------------+--------------+
|          1 |            2 |
|          2 |            1 |
|          3 |            1 |
|          4 |            0 |
+------------+--------------+


-- LEvel 3 Intermedidate SQL:

-- find second highest order amount


select max(amount) from orders where amount < (
  select max(amount) from orders );

  +-------------+
| max(amount) |
+-------------+
|    40000.00 |
+-------------+

-- find customer whose placed more than 1 orders

select c.name,c.CustomerId,count(o.OrderId) from Customer c 
left join Orders o on o.CustomerId =c.CustomerId
group by c.CustomerId,c.name
having count(o.OrderId) > 1;




+-------+------------+------------------+
| name  | CustomerId | count(o.OrderId) |
+-------+------------+------------------+
| Clark |          1 |                2 |
+-------+------------+------------------+


-- find the highest order for each customer

select c.name,MAX(o.amount) as maximum_order_amount from Customer c
inner join Orders o on o.CustomerId=c.CustomerId
group by c.CustomerId,c.name;

+-------+----------------------+
| name  | maximum_order_amount |
+-------+----------------------+
| Clark |             50000.00 |
| Dave  |             20000.00 |
| Ava   |             10000.00 |
+-------+----------------------+

-- find top three highest orders;

select * from Orders order by amount desc limit 3;

+---------+------------+----------+
| OrderId | CustomerId | amount   |
+---------+------------+----------+
|       1 |          1 | 50000.00 |
|       4 |          1 | 40000.00 |
|       2 |          2 | 20000.00 |
+---------+------------+----------+



-- find customer whose doesnot have the orders using not exists

select * from customer c where NOT exists(select 1 from Orders o 
where o.CustomerId=c.CustomerId)
;

+------------+-------+-------------+
| CustomerId | name  | email       |
+------------+-------+-------------+
|          4 | Vibin | vibib@gmail |
+------------+-------+-------------+
```





