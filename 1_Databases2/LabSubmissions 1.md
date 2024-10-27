You are required to submit your work as a single ZIP file containing:
- SQL code
- A pdf describing, for each lab/question, your design choices. For each lab, this is what you need to submit:

# <mark style="background: #69E772;">LAB 1:</mark>

### <mark style="background: #69E772;">Exercise 1:</mark>

![](https://i.imgur.com/Uy5nNrX.png)

<mark style="background: #69E772;">Task:</mark> the relational schema (table diagrams with primary/foreign keys) of your solution + explanation (no code is required)

<mark style="background: #69E772;">Diagram:</mark>
![](https://i.imgur.com/O9FKVPq.png)

<mark style="background: #69E772;">Code:</mark>
```plSQL
drop table if exists car;
drop table if exists teddy;
drop table if exists toy;

create table toy (
	uid VARCHAR(20) primary KEY UNIQUE NOT NULL,
	price VARCHAR(10),
	name VARCHAR(20));

create table teddy (
	uid VARCHAR(20) primary KEY UNIQUE NOT NULL,
	age VARCHAR(10),
	material VARCHAR(20),
	constraint uid_fk foreign key (uid) references toy(uid));

create table car (
	uid VARCHAR(20) primary KEY UNIQUE NOT NULL,
	engine_size VARCHAR(10),
	petrol_or_diesel VARCHAR(10),
	constraint uid_fk foreign key (uid) references toy(uid));

INSERT INTO toy VALUES ('860', '10', 'Bear'), ('310', '1.8', 'petrol');
INSERT INTO teddy VALUES ('860', '14', 'Felt');

--INSERT INTO car VALUES ();
select * from toy, teddy WHERE toy.uid = teddy.uid;
```

<mark style="background: #69E772;">Explanation:</mark>
The toy tables acts as a superclass to the individual toys like toy and teddy. All toys will have a name and price attribute but the toys have the attributes unique to them split into their own tables. This is easily extensible as more tables to represent different toys can be added. It is also storage-efficient as redundant rows are not added to the main toy table.
### <mark style="background: #69E772;">Exercise 2:</mark>
- a) for each situation, show a diagram (code is not required, but it can be added instead of the diagram)

```plSQL
-- EXERCISE 2
-- AA.
-- Table for E1 (Entity1) E1--(1,1)--R--(0,*)--E2 
drop table if exists entity2;
drop table if exists entity1;

CREATE TABLE entity1 (
    k1 INT PRIMARY KEY
);

-- Table for E2 (entity2)
CREATE TABLE entity2 (
    k2 INT PRIMARY KEY,      
    entity1_k1 INT,          
    FOREIGN KEY (entity1_k1) REFERENCES entity1(k1)
);

-- AB.
drop table if exists entity4;
drop table if exists entity3;

-- Table for E3 (Entity3) E3--(1,1)--R--(0,1)--E4
CREATE TABLE entity3 (
    k3 INT PRIMARY KEY
);

-- Table for E4 (Entity4)
CREATE TABLE entity4 (
    k4 INT PRIMARY KEY,
    entity3_k3 INT UNIQUE,
    FOREIGN KEY (entity3_k3) REFERENCES entity3(k3)
);

-- AC.
drop table if exists entity6;
drop table if exists entity5;

-- Table for E5 (Entity5)
CREATE TABLE entity5 (
    k5 INT PRIMARY KEY
);

-- Table for E6 (Entity6)
CREATE TABLE entity6 (
    k6 INT PRIMARY KEY,        
    entity5_id INT,    
    FOREIGN KEY (entity5_id) REFERENCES entity5(k5) ON DELETE SET NULL
);
```

# <mark style="background: #FF5582A6;">DERV ADD THE ENTITY RELATIONSHIP PHOTO HERE</mark>

- b) Explanation of your answers
-- B.

-- Yes. it is a one-to-many relationship.

- c) Your relational diagram + explanation

<mark style="background: #69E772;">Cinema Code:</mark>
```plSQL
drop table if exists booking;
drop table if exists showing;
drop table if exists screen;
drop table if exists customer;
drop table if exists movie;
drop table if exists cinema;

create table cinema(
	uid varchar(20) primary key unique not null, 
	cin_location varchar(50), 
	cin_name varchar(50), 
	contactNum varchar(15), 
	noScreens varchar(3)
);

create table movie(
	uid varchar(20) primary key unique not null,
	title varchar(50),
	duration varchar(20),
	rating varchar(20)
);

create table customer(
	username varchar(20) primary key unique not null,
	customer_password varchar(20),
	dob date
);

create table screen(
	uid varchar(20) primary key unique not null,
	cinema varchar(20),
	screenNo varchar(3),
	noSeats varchar(5),
	constraint screen_FK FOREIGN key (cinema) REFERENCES cinema(uid)
);

create table showing(
	uid varchar(20) primary key unique not null,
	screenNo varchar(3),
	movie varchar(20),
	showing_time time,
	constraint screen_FK FOREIGN key (screenNo) REFERENCES screen(uid),
	constraint movie_FK FOREIGN key (movie) REFERENCES movie(uid)
);

create table booking(
	bookingNo varchar(20) primary key unique not null,
	customer varchar(20),
	noChildTickets varchar(4),
	noAdultTickets varchar(4),
	showing varchar(20),
	seats varchar(20),
	price float(2),
	constraint showing_FK FOREIGN key (showing) REFERENCES showing(uid),
	constraint customer_FK FOREIGN key (customer) REFERENCES customer(username)
);
```

# <mark style="background: #FF5582A6;">DERV ADD THE CINEMA RELATIONSHIP PHOTO HERE</mark>
# <mark style="background: #69E772;">LAB 2:</mark>


SQL code for PART 1 and PART 2 with explanation of your code

# <mark style="background: #69E772;">LAB 3:</mark>

Exercise 1: SQL code of your TRIGGER/FUNCTION with explanation
Exercise 2: SQL code of your TRIGGER/FUNCTION with explanation

# <mark style="background: #69E772;">LAB 4:</mark>

Exercise 1: Submit the structure of the tables (or diagrams), no code is required
Exercise 2: Submit the structure of the tables (or diagrams) + SQL code

# <mark style="background: #69E772;">LAB 5:</mark>

Exercise 1: details of each insertion (each step should be presented
showing the tree before and after the insertion of a number)
Exercise 2: same as exercise 1
Exercise 3: show and explain your computation in your document
Exercise 4: write the answers to each question in your document (no code is needed)

The deadline for the submission is 3rd November end of the day
Demo will start Monday 4th of November, and they will run for 3 Mondays.
You will demo to your lab assistant. Each demo is about 15 mins
The lab assistant will ask you to demo and explain your lab work. You will have no time
to demo all your work, the lab assistant will ask you about specific exercises.
Without a demo, you will not receive any mark for your labs.
20% of your final marks will be allocated for the first demo. The final marks are based on
the clarity of your explanations, your design choices, the implementation of your
solution and on how many labs you have completed.
During the demos, lab will continue as usual. There will be 4 shorter labs in the second
batch of labs.