### <mark style="background: #69E772;">Joins:</mark>

<mark style="background: #69E772;">When do I use:</mark>  
- JOIN ... USING  
- JOIN... ON  
- LEFT JOIN  
- RIGHT JOIN  
- FULL OUTER JOIN

Observe the queries on the next slide.  
- Assuming you will solve them with a join, note :  
- The most appropriate type of join.  
- The efficiency of your query.  
- Upload and run the 'Builder Join problems' SQL file in your Builder schema.
![](https://i.imgur.com/pLUASLs.png)

### <mark style="background: #69E772;">Aggregation:</mark>

```SQL
SELECT [aggregate function], [aggregating attribute set]  
FROM [set of tables]  
[GROUP BY [aggregating attribute set]]  
[WHERE [condition calculated on each row]]  
[HAVING [condition calculated on aggregate result]];
```

Used to give summary information.  

Can be sub-grouped.  

Can be filtered on the aggregate result.  

Upload and run the 'Builder Aggregate problems' SQL file in your Builder schema.

![](https://i.imgur.com/ssqWd4N.png)

### <mark style="background: #69E772;">Windowing:</mark>

Window functions allow us to look at each row, with summary information alongside.  

We will use a different example to learn.  
- Upload and run the SQL file 'WinFunCreate.SQL' with sample tables.  
- Upload and individually run the queries in '

### <mark style="background: #69E772;">Create the tables:</mark>

```SQL
Create TABLE product_groups (  
group_id serial PRIMARY KEY,  
group_name VARCHAR (255) NOT NULL  
);  

Create TABLE products (  
product_id serial PRIMARY KEY,  
product_name VARCHAR (255) NOT NULL,  
price DECIMAL (11, 2),  
group_id INT NOT NULL,  
FOREIGN KEY (group_id) REFERENCES product_groups (group_id));
```

### <mark style="background: #69E772;">Add rows:</mark>

```SQL
INSERT INTO  
product_groups  
(group_name)  
VALUES  
('Smartphone'),  
('Laptop'),  
('Tablet');
```

```SQL
INSERT INTO products  
(product_name, group_id,price)  
VALUES  
('Microsoft Lumia', 1, 200),  
('HTC One', 1, 400),  
('Nexus', 1, 500),  
('iPhone', 1, 900),  
('HP Elite', 2, 1200),  
('Lenovo Thinkpad', 2, 700),  
('Sony VAIO', 2, 700),  
('Dell Vostro', 2, 800),  
('iPad', 3, 700),  
('Kindle Fire', 3, 150),  
('Samsung Galaxy Tab', 3, 200);
```

### <mark style="background: #69E772;">Run the queries - individual rows:</mark>

```SQL
select * from products  
join product_groups using (group_id);
```

![](https://i.imgur.com/cSDj0GC.png)


### <mark style="background: #69E772;">Run an aggregate</mark>

```SQL
-- get averages for each group  
SELECT group_name, AVG (price)  
FROM products  
JOIN product_groups USING (group_id)  
GROUP BY group_name;
```

### <mark style="background: #69E772;">Introducing the windows concept:</mark>

Windows functions allow you to combine the  
two:

```SQL
SELECT product_name, price, group_name, AVG (price) OVER (  
	PARTITION BY group_name)  
FROM products  
JOIN product_groups 
USING (group_id);
```

![](https://i.imgur.com/jJ5wXcV.png)

This gives a row for every product, with its group name and the aggregate average over the group.  

The <mark style="background: #69E772;">partition</mark> by clause tells the SQL engine how to sub-group the rows.

### <mark style="background: #69E772;">More advanced functions:</mark>

The ``ROW_NUMBER()``, ``RANK()``, and ``DENSE_RANK()`` functions assign an integer to each row based on its order in its result set.  

``FIRST_VALUE`` and ``LAST_VALUE`` pick out first and last items in a partition  

``LAG`` and ``LEAD`` allow each row to be compared  
with the previous / next row.

<mark style="background: #69E772;">ROW_NUMBER():</mark>

The ROW_NUMBER() function assigns a  sequential number to each row in each partition.  

```SQL
SELECT product_name, group_name, price, ROW_NUMBER () OVER (  
	PARTITION BY group_name  
	ORDER BY price)  
FROM products  
JOIN product_groups USING (group_id);
``` 

Run this query to see the result.

<mark style="background: #69E772;">RANK():</mark>

The RANK() function assigns ranking within an ordered partition.  

If rows have the same values, the RANK() function assigns the same rank, with the next ranking(s) skipped.  

```SQL
SELECT product_name, group_name, price, RANK () 
OVER (  
	PARTITION BY group_name  
	ORDER BY price)  
FROM products  
JOIN product_groups USING (group_id);
```

Run this query to see the result.

<mark style="background: #69E772;">DENSE_RANK():</mark>

The ``DENSE_RANK()`` function assigns a rank to each row within an ordered partition, but the ranks have no gap. i.e. the same ranks are assigned to multiple rows and no ranks are skipped.  

```SQL
SELECT product_name, group_name, price, DENSE_RANK () OVER (  
PARTITION BY group_name  
ORDER BY price)  
FROM products  
JOIN product_groups USING (group_id);
```

Run this query to see the result. Do you see how it differs from the previous one?

<mark style="background: #69E772;">First_value and Last_value:</mark>

The ``FIRST_VALUE()`` function returns a value evaluated against the first row within its partition.  

```SQL
SELECT product_name, group_name, price, FIRST_VALUE  
(price) OVER (  
	PARTITION BY group_name  
	ORDER BY price  
) AS lowest_price_per_group  
FROM products  
JOIN product_groups USING (group_id);
```

``LAST_VALUE()`` returns a value evaluated against the last row in partition.

```SQL
SELECT product_name, group_name, price, LAST_VALUE (price) OVER (  
	PARTITION BY group_name  
	ORDER BY price RANGE BETWEEN UNBOUNDED PRECEDING  
	AND UNBOUNDED FOLLOWING) AS highest_price_per_group  
FROM products  
INNER JOIN product_groups USING (group_id);
```

The default frame clause is ``RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW``. ... unbounded following includes all rows.  

This one is a little unusual – experiment to see what happens if you take out the extra clause.

### <mark style="background: #69E772;">LAG and LEAD – Compare adjacent rows in a group.</mark>

The LAG() function has the ability to access data from the previous row, while the LEAD() function can access data from the next row.  

Both <mark style="background: #69E772;">LAG()</mark> and <mark style="background: #69E772;">LEAD()</mark> functions have the same syntax as follows:  
- ``LAG (expression [,offset] [,default]) over_clause;``  
- ``LEAD (expression [,offset] [,default]) over_clause;``  

In this syntax:  
- <mark style="background: #69E772;">expression</mark> – a column or expression to compute the returned value.  
- <mark style="background: #69E772;">offset</mark> – the number of rows preceding ( LAG)/ following ( LEAD) the current row.  
- It defaults to 1.  
- <mark style="background: #69E772;">default</mark> – the default returned value if the offset goes beyond the scope of  the window. The default is ``NULL`` if you skip it.

The following statement uses the <mark style="background: #69E772;">LAG()</mark> function to return the prices from the previous row and calculates the difference between the price of the current row and the previous row.  

```SQL
SELECT product_name, group_name, price,  
lag(price, 1) OVER (  
PARTITION BY group_name  
ORDER BY price) "Previous Price",  
price - lag(price, 1) OVER (  
PARTITION BY group_name  
ORDER BY price) "Current - Previous Price"  
FROM products  
JOIN product_groups USING (group_id);
```

The following statement uses the <mark style="background: #69E772;">LEAD()</mark> function to return the prices from the next row and calculates the difference between the price of the current row and the next row.

```SQL
SELECT product_name, group_name, price,  
LEAD (price, 1) OVER ( PARTITION BY group_name  
ORDER BY price  
) AS next_price,  
price - LEAD (price, 1) OVER ( PARTITION BY group_name  
ORDER BY price  
) "Current - Next Price"  
FROM products  
JOIN product_groups USING (group_id);
```

### <mark style="background: #69E772;">Builder schema window functions practice:</mark>

1. Select each supplier name and the ``stock_code`` and ``stock_description`` of each stock item that supplier supplies.  
2. Select each supplier name and average ``unit_price`` of stock that supplier supplies.  
3. Select each supplier name, the ``stock_code``, ``stock_description``, ``unit_price`` and average ``unit_price`` for that supplier for each stock item that supplier supplies.  
4. Select each supplier name, the ``stock_code``, ``stock_description``, ``unit_price`` and rank of that price for that supplier for each stock item that supplier supplies.  
5. As above, but ``dense_rank()``  
6. Use ``lag()`` and ``lead()`` to compare item prices from a supplier.  
7. Use ``first_value()`` and ``last_value()`` to find highest and lowest ``unit_price`` per supplier.

### <mark style="background: #69E772;">Sets:</mark>

UNION, INTERSECT, EXCEPT  

Combining to provide a pattern for solving problems.  

Download and run "Builder SET problems.SQL"  

Fill in the gaps.

![](https://i.imgur.com/qF5u5bJ.png)


### <mark style="background: #69E772;">BUILDER SET QUERIES:</mark>

![](https://i.imgur.com/fXWgW7U.png)

### <mark style="background: #69E772;">Outline:</mark>

Using ‘in’ and ‘not in’  

Using reflexive queries, multiple nesting and other uses  

Use of EXISTS and NOT EXISTS  

Correlated sub-queries  

Join terminology  

Relational Divide  

Problem abstraction and using a template  

Using views to simplify queries.

### <mark style="background: #69E772;">Staff and customer orders:</mark>

![](https://i.imgur.com/EFEyUWY.png)


### <mark style="background: #69E772;">Expr in (sub-select):</mark>

Return the names of customers who have not collected their orders.

```SQL 
select customer_name  
from b2_customer  
Where Customer_id in  
(select customer_id  
from b2_corder  
where staffissued is null);
```

![](https://i.imgur.com/WoIwDtl.png)

Do we have suppliers in our supplier table who don’t supply any stock?

![](https://i.imgur.com/OlAxuNT.png)

### <mark style="background: #69E772;">Solution:</mark>

```SQL
SELECT supplier_name  
FROM b2_supplier  
WHERE supplier_id NOT IN  
(SELECT supplier_id from b2_STOCK);
```

Run this code from the ExtraExamples.sql file.