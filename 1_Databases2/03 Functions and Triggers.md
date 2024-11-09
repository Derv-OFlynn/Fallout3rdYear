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
- ``INSERT``  
- ``UPDATE``
- ``DELETE``  

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

To log these actions, we must  
1. Set up a table into which the ``TRIGGER`` can insert rows.  
2. Attach a ``TRIGGER`` to an ``OPERATION`` on a ``TABLE``.  

i.e. we attach a trigger to  
- An ``INSERT`` on ``B2_STOCK`` table.  
- An ``UPDATE`` on ``B2_STOCK`` table.  
- A ``DELETE`` on ``B2_STOCK`` table

<mark style="background: #69E772;">Set up the log table:</mark>

```SQL
create table stock_log(  
stock_code char(5),  
saleprice numeric(10,2),  
costprice numeric(10,2),  
stock_level numeric(7,0),  
username varchar(80),  
changedate date);
```

### <mark style="background: #69E772;">Triggers:</mark>

We will set up:  
• A row level INSERT and update audit trigger.  
• A row level INSERT and UPDATE constraint trigger.

```SQL
CREATE or replace FUNCTION audit_stock() RETURNS trigger AS $audit_stock$  
DECLARE  
	uname varchar(80);  
	cdate date;  
BEGIN  
select user into strict uname;  
	select now() into strict cdate;  
	insert into stock_log values (new.stock_code, new.unit_price, new.unitcostprice,  
new.stock_level, uname, cdate);  
return new;  
END;  
$audit_stock$ LANGUAGE plpgsql;  

CREATE or replace TRIGGER audit_stock BEFORE INSERT OR UPDATE ON b2_stock  
	FOR EACH ROW EXECUTE FUNCTION audit_stock();
```

<mark style="background: #69E772;">Execute the trigger:</mark>

```SQL
insert into b2_stock values ('K144','Coat Hooks', 8.99, 5.00, 30,10,1);  
select * from stock_log;
```

Output was: `K144 8.99 5.00 30 G99999999 2023-10-07`

### <mark style="background: #69E772;">Trigger fired by the SQL operation:</mark>

The operation works as normal on the table in the database, but it now fires a trigger.  
- The ``TRIGGER`` adds a row to the ``logtable``.  
- While the ``INSERT`` adds a row to the ``b2_stock`` table,  

Other operations: Triggers can be adapted to work on ``UPDATEs`` or ``DELETEs``.

### <mark style="background: #69E772;">Audit Trails:</mark>

When an INSERT ... FOR EACH ROW... trigger is active, it has access to the new values that the INSERT is trying to put into the table.  

These values can be accessed by preceding the attribute name with new.  
- E.g. to get the value that the insert is trying to put into the ``stock_code`` column in the table, we can reference ``new.stock_code``

### <mark style="background: #69E772;">Data available to INSERT trigger:</mark>

![](https://i.imgur.com/6g34o78.png)

![](https://i.imgur.com/fnav7AJ.png)


### <mark style="background: #69E772;">Who added rows to the subject table?</mark>

Create a table to hold the log of changes. Needs to know: 
- username, 
- date, 
- st_name
- st_id.  

Create a function 'audit_student', when someone performs 'INSERT' on the STUDENT table, record:  
- The student name 'st_name'  
- The generated student id 'st_id'  
- The username  
- The date and time of the operation.  

Make a trigger from the function  

Perform one of the triggering operations and look at the log.

```mySQL
CREATE or replace FUNCTION ... RETURNS trigger AS $...$  
DECLARE  
	uname varchar(80);  
	cdate date;  
BEGIN  
	select user into strict uname;  
	select now() into strict cdate;  

	insert into ... values (..., uname, cdate);  
return new;  
END;  
$...$ LANGUAGE plpgsql;  
CREATE or replace TRIGGER ... BEFORE ... ON ...  
FOR EACH ROW EXECUTE FUNCTION ...();
```

### <mark style="background: #69E772;">Activate the trigger:</mark>

From the schema that owns 'student':  
- Insert into student (st_name) values ('Delia');  
- Select from your log table.  

From G99999999:  
- ``select "Sample".addstudent('Deirdre');``  

Did it work? What would you need to do to make it work?


## <mark style="background: #69E772;">Constraint Triggers:</mark>

<mark style="background: #69E772;">Declarative Constraints:</mark>

Where possible, the state of the data in the database is guarded by declarative constraints. E.G:

```plSQL
CREATE TABLE B2_SORDER (  
SORDERNO SERIAL PRIMARY KEY,  
SORDERDATE DATE  
DEFAULT CURRENT_DATE NOT NULL,  
DELIVEREDDATE DATE,  
SUPPLIER_ID INTEGER  
REFERENCES B2_SUPPLIER NOT NULL,  
CONSTRAINT DATECHECK  
CHECK(DELIVEREDDATE >SORDERDATE));
```

### <mark style="background: #69E772;">Limitations on CHECK constraint:</mark>
  
<mark style="background: #69E772;">The CHECK constraint:</mark>  
- Must be Boolean expression  
- Can only use values in the current row  
- Cannot contain sub-queries, sequences or some functions.  

<mark style="background: #69E772;">We need to be able to:</mark>  
- Check data in other rows or even tables.  
- Cause the operation to fail if it breaks the rules.

### <mark style="background: #69E772;">Triggering failure</mark> 

Constraint trigger  

<mark style="background: #69E772;">In a function:</mark>  
- Use SQL statements to get the data that needs to be checked.  
- Perform the check.  
- If the check fails, raise a user-defined exception.  

Create a trigger to fire before the operation, executing the function.

### <mark style="background: #69E772;">Recalling the builder schema:</mark>

When a customer order line is added, the customer   specifies a quantity required.  

Is there enough stock? Check the ``stock_level`` in the stock table.

![](https://i.imgur.com/QEOoEDx.png)

<mark style="background: #69E772;">Creating the function and trigger:</mark>

```plSQL
CREATE FUNCTION check_stock() RETURNS trigger AS $check_stock$  
DECLARE  
	QTY INTEGER;  
BEGIN  
	SELECT STOCK_LEVEL INTO QTY FROM B2_STOCK  
		WHERE STOCK_CODE = NEW.STOCK_CODE;  
	IF QTY - NEW.QUANTITYREQUIRED < 0 THEN  
		RAISE exception '% not enough stock for this order', new.corderno;  
	END IF;  
	return new;  
END;  
$check_stock$ LANGUAGE plpgsql;  

CREATE TRIGGER check_stock BEFORE INSERT OR UPDATE ON b2_corderline  
	FOR EACH ROW EXECUTE FUNCTION check_stock();
```

<mark style="background: #69E772;">Testing the trigger:</mark>

![](https://i.imgur.com/kUWCbnk.png)

<mark style="background: #69E772;">Finding the trigger:</mark>

![](https://i.imgur.com/VbnyRkI.png)

<mark style="background: #69E772;">Drop a trigger:</mark>

The syntax for a dropping a Trigger is:  
``DROP TRIGGER trigger_name;``

### <mark style="background: #69E772;">Sample triggers for BUILDER:</mark>

Insert trigger that could go on corderline:  
- Check there is enough stock before selling.  
- Reject invalid transactions  
- Record reorder requirements  

Update trigger on supplier order delivery date  
- Check that date is not already there  
- Check that date is not in the future.

### <mark style="background: #69E772;">Built-in variables available in a trigger:</mark>

<mark style="background: #69E772;">NEW record</mark> - new database row for INSERT/UPDATE operations in row-level triggers. This variable is null in statement-level triggers and for DELETE operations.  

<mark style="background: #69E772;">OLD record</mark> - old database row for UPDATE/DELETE operations in row-level triggers. This variable is null in statement-level triggers and for INSERT operations.  

<mark style="background: #69E772;">TG_NAME name</mark> - name of the trigger which fired.  

<mark style="background: #69E772;">TG_WHEN text</mark> - BEFORE, AFTER, or INSTEAD OF, depending on the trigger's definition.  

<mark style="background: #69E772;">TG_LEVEL text</mark> - ROW or STATEMENT, depending on the trigger's definition.  

<mark style="background: #69E772;">TG_OP text</mark> - operation for which the trigger was fired: INSERT, UPDATE, DELETE, or TRUNCATE.  

<mark style="background: #69E772;">TG_TABLE_NAME name</mark> - table that caused the trigger invocation.  

<mark style="background: #69E772;">TG_TABLE_SCHEMA name</mark> - schema of the table that caused the trigger invocation.

### <mark style="background: #69E772;">Transactions and multiple users:</mark>

Concurrent usage  
- Enabling  
- Problems arising  
- ACID properties  

Commit and Rollback (Autocommit)  

Transaction modes

### <mark style="background: #69E772;">Concurrent Usage:</mark>

A schema has at least one role with full access.  

Other users can only manipulate data in your schema if you grant them privileges to do so.  

You can GRANT privileges to specific users, or to PUBLIC (all users).  

You can REVOKE privileges you have previously granted.  

Note: In PostgreSQL you must first:  
``GRANT USAGE ON SCHEMA <myschema> TO <other_user>;``

### <mark style="background: #69E772;">GRANT and REVOKE:</mark>

You can ``GRANT SELECT`` on ``<mytable>`` TO "G99999999";  

You can ``GRANT SELECT`` on ``<mytable>`` TO PUBLIC;  

You can ``GRANT INSERT`` on ``<mytable>`` to PUBLIC;  

Now everyone can add data!  

You can ``REVOKE INSERT`` on ``<mytable>`` FROM PUBLIC;  

Probably a good idea.  

GRANT ALL ON ``<mytable>`` TO PUBLIC;  

Probably NOT a good idea. Now everyone can INSERT, UPDATE, DELETE and SELECT your data.

### <mark style="background: #69E772;">What other privileges?</mark>

I can grant / revoke  
- SELECT, INSERT, UPDATE or DELETE on my tables or views to roles.  
- EXECUTE on functions or stored procedures.  

Note:  
- If the function / procedure does an INSERT, the grantee must be granted INSERT privileges on the table.  
- If the INSERT generates a new serial ID, the grantee must be granted UPDATE on the SEQUENCE.

### <mark style="background: #69E772;">Sample access:</mark>

If I want "G99999999" to be able to run the 'addstudent' function:

```plSQL
Grant usage on schema "Sample" to public;  
grant execute on function addstudent to "G99999999";  
grant insert on table student to "G99999999";  
grant update on table student to "G99999999";
```

### <mark style="background: #69E772;">Principle of least privilege:</mark>

“Only the minimum necessary rights should be assigned to a subject that requests access to a resource and should be in effect for the shortest duration necessary (remember to relinquish privileges).  
Granting permissions to a user beyond the scope of the necessary rights of an action can allow that user to obtain or change information in unwanted ways. Therefore, careful delegation of access rights can limit attackers from damaging a system. ”

https://www.us-cert.gov/bsi/articles/knowledge/principles/least-privilege  - United States Computer Emergency Readiness team.

### <mark style="background: #69E772;">Major weakness in security:</mark>

Granting all privileges on CREATE USER:  

“...I cannot think of any circumstances when ALL PRIVILEGES should be granted to anyone. It is simply unnecessary. Do the job correctly and find out the exact privileges needed for the job in hand and grant those. Granting all privileges is a security risk as it means the user having those privileges can do just about anything in your database.”  - Pete Finnigan, Oracle Security Expert

### <mark style="background: #69E772;">Locking and concurrency:</mark>

How to cope with multiple users conducting simultaneous transactions

### <mark style="background: #69E772;">Transactions:</mark> 

In the Builder Case Study we require transactions to:  

<mark style="background: #69E772;">Add an order:</mark>  
- Maybe add a customer  
- Add an order  
- Add one or more order lines to the order. Each new line means we need to adjust the remaining amount in the stock table.  
- Confirm (commit) or abandon (rollback) the order)  

<mark style="background: #69E772;">Ship an order:</mark>  
- Confirm that the stock has been handed over to the customer.  
- This requires an update of the order table.  

There are more.

### <mark style="background: #69E772;">Concurrent transactions (Builder)</mark>

![](https://i.imgur.com/RLcCe6n.png)

### <mark style="background: #69E772;">If it is a single-user system:</mark>

Fred will put in his order and the stock-level for the bicycle locks will go down to 5.  

Joe will try to order 7 locks and won’t be allowed.  

OR  

Joe will put in his order and stock-level for the locks will go down to 8.  

Fred will try to order 10 locks and won’t be allowed.  

But what if they are both are working at the same time?

### <mark style="background: #69E772;">Problems with Concurrency:</mark>

Concurrent transaction can cause three kinds of database problems  
- Lost Update  
- Violation of Integrity Constraints  
- Inconsistent Retrieval

### <mark style="background: #69E772;">Lost update (Builder):</mark>

Apparently successful updates can be overwritten by other transactions.

```plSQL
Initial Balance = 100
```

![](https://i.imgur.com/BvNELAW.png)

![](https://i.imgur.com/PsFC1j5.png)

Either update could go a fraction of a second earlier and overwrite the other.

### <mark style="background: #69E772;">Inconsistent Retrieval (Dirty Reads):</mark>

If transaction are allowed to read the partial results of incomplete transactions, they can obtain an inconsistent view of the DB (dirty or unrepeatable reads).

### <mark style="background: #69E772;">Concurrency Control:</mark>  

<mark style="background: #69E772;">Transaction:</mark> the basic unit of work in a RDBMS  

<mark style="background: #69E772;">Properties of a transaction:</mark>  
- ATOMICITY  
- CONSISTENCY  
- ISOLATION  
- DURABILITY

![](https://i.imgur.com/LQEFiBm.png)

### <mark style="background: #69E772;">A.C.I.D properties:</mark>

<mark style="background: #69E772;">Atomicity:</mark> the is the “all or nothing” property ; a transaction is an indivisible unit of work  

<mark style="background: #69E772;">Consistency:</mark> transactions transform the DB from one consistent state to another consistent state

<mark style="background: #69E772;">Isolation:</mark> transactions execute in isolation i.e. the partial effect of one transaction is not  visible to other transactions.  

<mark style="background: #69E772;">Durability (aka Persistence):</mark> the effect of a successfully completed (i.e. committed) transaction are permanently recorded in the DB and cannot be undone.

### <mark style="background: #69E772;">Conflicting Operations:</mark>

If two transactions only read a data item, they do <mark style="background: #69E772;">not</mark> conflict and order is not important.  

If two transactions either read or write completely separate data items, they do not conflict and order is <mark style="background: #69E772;">not</mark> important.  

If one transactions writes a data item and another transaction reads or writes the same data item, the order of execution <mark style="background: #69E772;">is</mark> important.

### <mark style="background: #69E772;">Making changes persist:</mark>

When data is changed, it must be persisted, to ensure that the change takes.  

<mark style="background: #69E772;">E.g. a text editor:</mark>  
- ``SAVE`` will ``COMMIT`` your changes.  
- ``QUIT`` will ``ROLLBACK`` your changes.  

<mark style="background: #69E772;">AUTOCOMMIT:</mark>  
- When this feature is ON, changes are persisted as soon as they happen. Similar to Google Docs.

### <mark style="background: #69E772;">AUTOCOMMIT, COMMIT and ROLLBACK:</mark>

Many modern database clients set ``autocommit`` on by default.

![](https://i.imgur.com/9rpddOY.png)

![](https://i.imgur.com/CEktyAp.png)

### <mark style="background: #69E772;">Transactions:</mark>

A transaction (or logical unit of work) is a sequence of SQL statements that ``postgreSQL`` treats as a single unit.  

<mark style="background: #69E772;">A transaction ends with a</mark>  
- commit,  
- rollback ,  
- any DDL statement which issues an implicit commit.

### <mark style="background: #69E772;">Implicit and explicit transactions:</mark>

<mark style="background: #69E772;">In autocommit mode:</mark>  
- Every SQL statement is considered to be a transaction  
- It has an implicit BEGIN before it.  
- It has an implicit COMMIT after it.  

TURN AUTOCOMMIT OFF!!!

![](https://i.imgur.com/3dDi43M.png)

### <mark style="background: #69E772;">Transactions and locking:</mark>

Transactions start with ``BEGIN``  
- When an ``INSERT``, ``UPDATE`` or ``DELETE`` takes place:  
- It locks the row that is being ``INSERTed`` / ``UPDATEd`` / ``DELETEd``  
- Other sessions cannot see the changes that are being made.  
- The lock holds until the transaction session is finished by issuing  
- ``COMMIT`` or ``ROLLBACK``

### <mark style="background: #69E772;">The transaction control commands:</mark>

<mark style="background: #69E772;">commit</mark> makes all changes since the beginning of a transaction permanent  

<mark style="background: #69E772;">rollback</mark> rolls back (undoes) all changes since the beginning of a transaction.  

<mark style="background: #69E772;">Other users:</mark>  
- cannot see the results of the transaction until it has been committed.  
- Can see the data as it was before the other user's transaction started!

### <mark style="background: #69E772;">Overview:</mark>

<mark style="background: #69E772;">Locking:</mark>  
- allows a user to take hold of a block for updating.  
- Prevents other users from modifying the same data.  
- Locks can create performance problems.  
- When one process locks, others are shut out.  
- There are several levels of locking.

<mark style="background: #69E772;">When modifying:</mark>  
- The transaction should place a lock until committed or rolled back.  
- This is known as data concurrency.

<mark style="background: #69E772;">Read-consistency:</mark>
- All processes can access (read) the original data as they were at the time the query began (uncommitted modification).

### <mark style="background: #69E772;">Row-level Locking (read consistency):</mark>

Each row can be locked individually.  

Locked rows can only be updated by the locking session.  

Other rows can be updated by other sessions.  

Other sessions can still read all rows.  

When other sessions read locked rows, they see the pre-locked values for the row.  

When the lock is released, by COMMIT or ROLLBACK, the new values are visible to other sessions.

### <mark style="background: #69E772;">Locking rows:</mark>

![](https://i.imgur.com/vPEjbjA.png)

### <mark style="background: #69E772;">Exclusive locks:</mark>

<mark style="background: #69E772;">Exclusive locks occur on ROWS when:</mark>  
- The row is ``INSERTed``  
- The row is ``DELETEd``  
- The row is ``UPDATEd``  
- The row is ``SELECTed``... FOR ``UPDATE``...

### <mark style="background: #69E772;">Deadlocks:</mark>

A deadlock can occur when two or more users are waiting for data locked by each other.  

Deadlocks prevent some transactions from continuing to work.  

The next example illustrates two transactions in a deadlock.

### <mark style="background: #69E772;">Example:</mark>

![](https://i.imgur.com/9CmPlp1.png)

### <mark style="background: #69E772;">Example explanation:</mark>

<mark style="background: #69E772;">At timepoint A:</mark>  
- no problem exists as each transaction has a row lock on the row it attempts to update.  
- Each transaction proceeds without being terminated.  
- However, each tries next to update the row currently held by the other transaction.  

<mark style="background: #69E772;">At timepoint B:</mark>  
- a deadlock results, because neither transaction can obtain the resource it needs to proceed or terminate.  
- It is a deadlock because no matter how long each transaction waits, the conflicting locks are held.

### <mark style="background: #69E772;">How to avoid Deadlocks:</mark>

Application developers can eliminate all risk of deadlocks by ensuring that transactions requiring multiple resources <mark style="background: #69E772;">always lock them in the same order.</mark>  

However, in complex applications, this is easier said than done, particularly if an ad hoc query tool is used.  

To be safe, you should adopt a strict locking order, but you must also <mark style="background: #69E772;">handle locking exceptions</mark>.  

To handle locking exceptions:  
- Pause for three seconds, and then retry the statement.  
- Or, roll back the transaction, wait 3 seconds and retry.