### Staplets:(10-11-2026)

Get order amount greater than 50000:


```sql
-- create
CREATE TABLE Customer (
  CustomerId INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT NOT NULL
);


CREATE TABLE Orders (
  OrderId INTEGER PRIMARY KEY,
  CustomerId INTEGER NOT NULL,
  amount TEXT NOT NULL
);
-- insert
INSERT INTO Customer VALUES (0001, 'Clark', 'deva@gmail');
INSERT INTO Customer VALUES (0002, 'Dave', 'deva1@gmail');
INSERT INTO Customer VALUES (0003, 'Ava', 'deva2@gmail');


-- insert
INSERT INTO Orders VALUES (0001, 0001, 50000);
INSERT INTO Orders VALUES (0002, 0002, 20000);
INSERT INTO Orders VALUES (0003, 0003, 10000);



SELECT name,email from Customer c
left Join Orders o on o.CustomerId=c.CustomerId
WHERE o.amount >= '50000';

+-------+------------+
| name  | email      |
+-------+------------+
| Clark | deva@gmail |
+-------+------------+

```

