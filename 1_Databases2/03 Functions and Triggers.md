### <mark style="background: #69E772;">Outline:</mark>

Where is the database?  
- Where do the programs work?  
- Parameters  
- Declaring variables  
- Verbose syntax IF...THEN...ELSE...END IF;

### <mark style="background: #69E772;">Where is the database?</mark>

The database is at the base of your application  

When you look at a software schematic, the data is almost always at the opposite end to the user.

### <mark style="background: #69E772;">Application layers:</mark>

![](https://i.imgur.com/EKm9CwY.png)

<mark style="background: #69E772;">The presentation layer:</mark> The user sees or interacts with this layer.  

<mark style="background: #69E772;">The business logic layer:</mark> Enforces the business rules  

<mark style="background: #69E772;">The data access layer</mark> enforces rules regarding the storage and access of information.

### <mark style="background: #69E772;">Databases in an application:</mark>

![](https://i.imgur.com/8jcCq0d.png)

### <mark style="background: #69E772;">Over the web:</mark>

![](https://i.imgur.com/tqIK1gW.png)

### <mark style="background: #69E772;">Apps use multiple databases:</mark>

![](https://i.imgur.com/13FTMUP.png)

# <mark style="background: #69E772;">Functions in postgreSQL</mark>

### <mark style="background: #69E772;">Function Skeleton:</mark>

```SQL
CREATE OR REPLACE FUNCTION <function name> (  
	<parameter-names parameter data types>)  
	RETURNS <return data type>  
	LANGUAGE plpgsql  
AS $function$  
DECLARE  
	<local variable names and datatypes>;  
BEGIN  
	<function logic, including return statement> 
EXCEPTION  
	<exeption logic>  
END;  
$function$;
```

### <mark style="background: #69E772;">Creating and running the function:</mark>

To create the function, the function code is run in a SQL code window.  
- See next slides for function code  
- This compiles the function and saves it in the schema.  

The function can be run in a SQL code window as  ``SELECT * from <function call with parameters>``;


![](https://i.imgur.com/uNXaAbX.png)

### <mark style="background: #69E772;">Parts of a function:</mark>

Name follows naming rules in PostgreSQL.  

Parameters are declared with a name and data type.  

The data type can be a standard data type, or can be inherited from a table column, suffixed with ``‘%type’``. This promotes data independence, E.g. customer_name b2_customer.customer_name%type;  
By default, parameters are ‘in out’ or pass by reference  – i.e if you change their values in the function, they retain the changed value in the calling environment.  

<mark style="background: #69E772;">Function logic:</mark> ALWAYS contains at least one SQL statement!

### <mark style="background: #69E772;">Declarations in addcustomer function:</mark>

We want to take in a customer’s name and optional address and add a row to the customer table. We want to return the new customer id.  

```SQL
CREATE OR REPLACE FUNCTION addcustomer(  
p_cname b2_customer.customer_name%type,  
p_caddr b2_customer.customer_address DEFAULT NULL)  
	RETURNS integer  
	LANGUAGE plpgsql  
AS $function$  
DECLARE  
	v_custid INTEGER;
```

### <mark style="background: #69E772;">Local variables and fixed size memory:</mark> 

Functions can only hold data in the declared section.  

This means:  
- When I SELECT, I must say where the data is going!!!!  
- All data that is SELECTed must be selected INTO a declared variable or area.  

Also, when inserting a row, we can return any part of the new row:  
```SQL
insert into b2_customer (customer_name, customer_address)  
values (p_cname, p_contactno) returning customer_id into v_custid;
``` 

The RETURNING keyword in PostgreSQL gives an opportunity to return from the insert or update statement the values of any columns after the insert or update was run.

### <mark style="background: #69E772;">Add a customer:</mark>

```SQL
create or replace FUNCTION ADDCUSTOMER(  
	p_cname b2_customer.customer_name%type,  
	p_caddr b2_customer.customer_address%type default NULL)  
	returns INTEGER AS  
$$  
DECLARE  
	v_custid INTEGER;  
BEGIN  
	insert into b2_customer (customer_name, customer_address)  
	values (p_cname, p_caddr) returning customer_id into v_custid;  
	RETURN v_custid;  
END;  
$$ LANGUAGE plpgsql
```

Looking more closely, you can call this function with one parameter.

### <mark style="background: #69E772;">Run the function in SQL:</mark>

```SQL
select addcustomer('Johnny  
Comelately','Hostel'); 
```

This returns the ``customer_id`` of the row that has just been added.

SQL code for ``addcustomer`` is in Brightspace under ``addcustomer.sql``  

It should be run in your BUILDER schema.

### <mark style="background: #69E772;">New model - Student - subject:</mark>

![](https://i.imgur.com/np5YJpu.png)

<mark style="background: #69E772;">Table contents:</mark>
![](https://i.imgur.com/W3E8dvg.png)

<mark style="background: #69E772;">Student passes module:</mark>

You now have 3 tables in your schema, with some data in them (shown on the next two slides).  

Write a function ``AddStudent`` that takes in a student name and returns the serial number that has been allocated as key to that row in the student table.  

A lot of the code is in ``PartAddStudent.sql``

### <mark style="background: #69E772;">Postgres Procedures:</mark>

These are similar to functions, but there is no RETURN.  

Procedures are initiated using CALL.  

Procedures are used to:  
- Carry out a process.  
- Often used to perform maintenance or upgrade tasks.  
- Often have iteration.

<mark style="background: #69E772;">Resources on brightspace:</mark>
- Create_tournament.sql  
- Make_matches procedure.sql

### <mark style="background: #69E772;">Example:</mark>

A club runs tournaments for its players. When a new tournament starts, the club must set up matches.  

Let's assume a new knockout tournament is taking place, with 64 players.  
- We want 32 first round matches.  
- 16 second round, 8 third round, 4 fourth round, 2 fifth round and a final (6th round).

![](https://i.imgur.com/uZH0Pah.png)

<mark style="background: #69E772;">We don't know:</mark>  
- what date they'll be  
- Who the players will be  
- What the scores will be  

Write a procedure to take in  
- the tournament key (Tkey)  
- The round number  
- The number of matches  

Add all the matches for that round.

### <mark style="background: #69E772;">Create the Procedure:</mark>

```SQL
create or replace procedure make_matches(  
p_tkey tournament.tkey%type,  
p_round match.tround%type,  
nomatches integer)  
LANGUAGE plpgsql  
AS $$  
	begin  
	for i in 1..nomatches loop  
	insert into match (tkey, tround, matchno)  
	values (p_tkey, p_round, i);  
	END loop;  
	end;  
$$;
```

Procedure, rather than function

Iteration can be done using a loop.

No return statement.

### <mark style="background: #69E772;">Call the procdure:</mark>

```SQL
call make_matches ('Ashe',1,16);  
call make_matches ('Ashe',2,8);  
call make_matches ('Ashe',3,4);  
call make_matches ('Ashe',4,2);  
call make_matches ('Ashe',5,1); 

select * from match;
```

### <mark style="background: #69E772;">Trapping exceptions:</mark>

Raise exceptions in the code, and return the database's own error messages.  

Before the END;insert the following: 

```SQL
exception 
when others then  
RAISE info 'Error Description:%',sqlerrm;  
raise info 'Error Code:%', SQLSTATE;
```

### <mark style="background: #69E772;">Back to theory:</mark>

The relational database offers the following protection:  
- Primary keys prevent adding duplicates  
- Check and references constraints prevent invalid data from being entered.  

Other requirements:  
- Further checks on INSERT, UPDATE and DELETE.  
- Privacy from unauthorized users  
- Atomicity to prevent concurrency issues

# <mark style="background: #69E772;">Triggers:</mark>

### <mark style="background: #69E772;">What is a trigger?</mark>

An action that is taken when some event occurs.  

The events we will address are Data Manipulation events:  
- INSERT, 
- UPDATE and 
- DELETE operations.

### <mark style="background: #69E772;">Piggyback:</mark>

The operation works as normal on the table in the database, but it now has a trigger, piggybacking on it.  

The ``TRIGGER`` can log events or constrain them.  

While the ``INSERT``, ``UPDATE`` or ``DELETE`` manipulate the table as intended.

![](https://i.imgur.com/iiGdqwR.png)

### <mark style="background: #69E772;">Reasons for triggers:</mark>

Triggers can be used for:  
- Logging user actions  (Who updated a staff member’s salary? When?)  
- Checking constraints  (I don’t want to sell stock I do not have. I don’t want a student to register for modules if they are already registered for 60 ECTS  credits worth. )

Other reasons: Automatically generate derived column values

### <mark style="background: #69E772;">Logging actions:</mark>

These triggers apply to:  
- INSERT  
- UPDATE
- DELETE  

To log these commands we need a log table.

### <mark style="background: #69E772;">To log actions:</mark>

When logging user actions, in general, we need to know:  
- What table is being changed.  
- What the change is (INSERT, UPDATE or DELETE).  
- Who has made the change.  
- When was the change made.  

This information tells us a little about the transaction. For future use we add:  
- Keyval, oldprice, newprice

### <mark style="background: #69E772;">Logging actions:</mark>