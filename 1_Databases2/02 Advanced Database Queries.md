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

### <mark style="background: #69E772;">NULL "problem":</mark>

```SQL
Select staff_no, reports_to  
from b2_staff;
```

![](https://i.imgur.com/hjWoBRC.png)

Get the names and staff numbers of staff who have nobody reporting to them.  

```SQL
select staff_no 
from b2_staff 
where staff_no 
not in (select reports_to from b2_staff);
```  

This query returns an empty set, because NOT IN cannot evaluate a column that has NULLs.

### <mark style="background: #69E772;">Using aggregates in sub-queries:</mark>

```SQL
SELECT stock_code,stock_description, unit_price 
FROM b2_stock  
WHERE unit_price > (
	SELECT AVG(unit_price) 
	FROM b2_stock);
```

![](https://i.imgur.com/Pqy6U3W.png)

This query returns the stock code, description and price of all stock items that cost more than the average unit price of any stock item.

### <mark style="background: #69E772;">EXISTS condition:</mark>

This returns a Boolean value of true or false.  

The result is true if the sub-query returns a non-empty set of values i.e. it’s true that a row exists.  

The sub-query is generally correlated to the outer query

The ``EXISTS`` condition is met if the sub-query returns at least one row.  

The syntax for the ``EXISTS`` condition is:  
```SQL
SELECT columns  
FROM tables  
WHERE EXISTS ( subquery );
``` 

The ``EXISTS`` condition can be used in any valid SQL statement - select, insert, update, or delete.

e.g.  
```SQL
select * from b2_stock where exists (select now());  

-- This is the same as  

Select * from b2_stock;  
because “select now()” returns the current date, so a value exists.```

because “select now()” returns the current date, so a value exists.

The following query will return no values:  
```SQL
select * from b2_stock where exists (  
select now()  
where 1 = 2);
```  

Because  
```SQL
select now() where 1 = 2
```  

returns no values.

### <mark style="background: #69E772;">CORRELATED SUB-QUERIES:</mark>

This is where the inner select statement refers to data defined in the outer select statement.

<mark style="background: #69E772;">Example 1 - EXISTS:</mark>
This select statement will return all records from the suppliers table where there is at least one record in the supplier order table with the same ``supplier_id``.  

It is a <mark style="background: #69E772;">correlated sub-query</mark>.

```SQL
SELECT *  
FROM b2_supplier s  
WHERE EXISTS  
	(select *  
	from b2_sorder o  
	where s.supplier_id = o.supplier_id);
```

![](https://i.imgur.com/8cGpCOy.png)

<mark style="background: #69E772;">Example #2 - NOT EXISTS:</mark>

The ``EXISTS`` condition can also be combined with the NOT operator.  

For example,  
```SQL
SELECT *  
FROM supplier s  
WHERE not exists (select * from sorder o  
where s.supplier_id = o.supplier_id);
```

<mark style="background: #69E772;">Example #3 - DELETE Statement:</mark> 

The following is an example of a delete statement that utilizes the EXISTS condition:

```SQL
DELETE FROM supplier s  
WHERE not EXISTS  
	(select *  
	from sorder o  
	where s.supplier_id = o.supplier_id);
```

<mark style="background: #69E772;">Correlated sub-query:</mark>  

```SQL
SELECT stock_code, stock_description, unit_price, supplier_id  
FROM b2_stock st  
WHERE unit_price > (  
SELECT AVG(unit_price) FROM b2_stock WHERE  
supplier_id = st.supplier_id);
```

This returns the stock code, description, price and supplier id of all stock items that cost more than the average stock item supplied by that supplier.

### <mark style="background: #69E772;">RELATIONAL DIVIDE:</mark>

Shows rows in one table that are related to all rows in another ``many:many`` table.  
e.g. Which students have passed ALL modules?

### <mark style="background: #69E772;">New Model - Student - subject:</mark>

![](https://i.imgur.com/Lp2Eui7.png)

<mark style="background: #69E772;">Table Contents:</mark>
![](https://i.imgur.com/yG2x8If.png)

<mark style="background: #69E772;">Reword the query:</mark> Return names of students where there does not exist a subject they haven't achieved.  

This double negative is part of DeMorgan's theorem.

<mark style="background: #69E772;">Who achieved everything?</mark>
![](https://i.imgur.com/WSgtVTJ.png)

```SQL
select st_name from student a  
where not exists (  
	select * from subject b  
	where not exists (  
		select * from acheivement x  
		where  
		x.st_id = a.st_id and  
		x.sb_id = b.sb_id));
```

### <mark style="background: #69E772;">Abstraction:</mark>

Return a list of occurrences of A related to ONLY n occurrences of B.  

Return a list of occurrences of A that are related to ALL occurrences of B  
- Return a list of A relate to ALL B where...  

Return a list of A that have no related occurrences in B.  

Return details of any A that is related to an occurrence in B  

Return a list of occurrences of A that are related to both occurrences B<sub>i</sub> and B<sub>j</sub> where B<sub>i</sub> , Bj<sub>j</sub> B∈  

Return a list of A that are related to Bi but not B<sub>j</sub> where B<sub>i</sub> , B<sub>j</sub> B∈  

Return a list of A that are related to either B<sub>i</sub> or B<sub>j</sub> but not both.

![](https://i.imgur.com/Dte2cWL.png)

### <mark style="background: #69E772;">Helpful hints:</mark>

If you are basing your answer on SET theory, it can be helpful to create views of the sets.  

E.g. List the names of customers who have bought blocks but not bought bricks. Start by creating a view:  
```SQL
create view boughtblock as  
select customer_name from b2_customer  
join b2_corder using (customer_id)  
join b2_corderline using (corderno)  
join b2_stock using (stock_code)  
where lower (stock_description) like  
'%block%'; 
```

What’s next?

![](https://i.imgur.com/gVa3Qsm.png)


<mark style="background: #69E772;">Who bought what?</mark>
To find a list of the customer names and what they bought, I would need:

![](https://i.imgur.com/J2tJWdZ.png)

<mark style="background: #69E772;">How did we do that?</mark>

By tracing a path through the relationships, we could see:  
- Which attributes we wanted to show  
- What tables they were in  
- Which attributes we needed to join the tables  
- Where were the attributes that we were testing in the conditions?

### <mark style="background: #69E772;">Using Views:</mark>

<mark style="background: #69E772;">Generalising the query:</mark> 
- Which customers bought the item with ``stock_description`` 'Phillips screwdriver'?  
- What did customer named ‘John Flaherty’ buy?  

To do that, I can store my query in a view, and query the view.

<mark style="background: #69E772;">Create the view:</mark>
```SQL
Create view custbought as  
Select customer_name, stock_description  
From b2_customer  
Join b2_corder using (customer_id)  
Join b2_corderline using (corderno)  
Join b2_stock using (stock_code);
```

<mark style="background: #69E772;">Query the view:</mark>
```SQL
Select customer_name from custbought where   stock_description = 'Phillips screwdriver';
```

<mark style="background: #69E772;">Build the queries using views:</mark>

![](https://i.imgur.com/tgM2b9o.png)

![](https://i.imgur.com/Y7DYEe6.png)

![](https://i.imgur.com/jYlfK73.png)

### <mark style="background: #69E772;">Using views:</mark>

I’d like to know :  
- Students who passed Maths but not Geography? ``(A – B)``  
- Students who passed Geography but not Maths? ``(B – A)``  
- Students who passed both Geography and Maths? ``(A ∩ B)``  
- Students who passed either Geography or Maths? ``(A U B)``  
- Students who passed either Geography or Maths, but not both? ``A xor B (A U B) - (A ∩ B) `` 
- Students who only passed Maths? ``(A - ¬A)``  
- Use the ``SampleDivide.sql`` file to experiment.  
- Add and delete rows from the achievement table to see what difference it makes.

### <mark style="background: #69E772;">Transferring our skills to the builder schema:</mark>

What about :  
- Customers who bought a workbench but no timber?  ``(A – B)``  
- Customers who bought timber but no workbench? ``(B – A)``  
- Customers who bought both timber and a workbench? ``(A ∩ B)``  
- Customers who bought either timber or a workbench? ``(A U B)``  
- Customers who bought either timber or a workbench, but not both? ``A xor B (A U B) - (A ∩ B)``  
- Customers who only bought a workbench?``(A - ¬A``

### <mark style="background: #69E772;">What is the shape of our tables?</mark>

ERDs start to get complex when there are many:many relationships.  
- Students eating types of crisp  
- Students sitting modules  
- Customers buying stock  

We can use SET theory to form a template for  common queries.

![](https://i.imgur.com/KcZdxHE.png)

<mark style="background: #69E772;">A trivial example:</mark>
![](https://i.imgur.com/dJM8nMi.png)

<mark style="background: #69E772;">Who ate every type of crisp?</mark>
```SQL
SELECT CN_NAME FROM CR_CONSUMER A  
WHERE NOT EXISTS (  
	SELECT * FROM CR_CRISP_TYPE B 
	WHERE NOT EXISTS (  
		SELECT * FROM CR_HAS_EateN X  
		WHERE A.CONSUMERID =  X.CONSUMERID AND B.CRISPKEY = X.CRISPKEY  
	)  
);
```

![](https://i.imgur.com/Z1PXSoQ.png)

<mark style="background: #69E772;">Helping the divide:</mark>
If I want a list of non-key values in A for rows that are  associated with all occurrences of B:

![](https://i.imgur.com/Rp4hHc5.png)

![](https://i.imgur.com/JCqPou0.png)

<mark style="background: #69E772;">Slightly more obscure:</mark>

Who bought all the stock items supplied by Buckleys?  

Where are A, X and B?  
- A must be a table or view with the identifying key to customer name, joined to X.  
- B must be a table or view with the identifying key to the stock items supplied by Buckleys, joined to X.  
- X must be a weak entity, with a many:1 link to A  and to B.

![](https://i.imgur.com/AR93bCU.png)

<mark style="background: #69E772;">The views:</mark>
![](https://i.imgur.com/yFLnT7L.png)

![](https://i.imgur.com/jRGaGAN.png)


<mark style="background: #69E772;">The final query:</mark>
![](https://i.imgur.com/36nQ4lu.png)

![](https://i.imgur.com/CtfBwhN.png)
