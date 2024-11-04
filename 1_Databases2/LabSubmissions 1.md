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

<mark style="background: #69E772;">Relational Diagram:</mark>
![](https://i.imgur.com/dKzX4XV.jpeg)

<mark style="background: #69E772;">Explanation:</mark>
I first made a cinema table, each entry represents one of the company's 50 cinemas. The UID column is the primary key and is used to uniquely identify each cinema. This means that it does not matter if cinemas change their names or have the same name as other cinemas. The table also stores the cinema's location, number, name and number of screen, as required.

There is then a movie table. Each movie has a UID, as some movies have the same names. The entries store the title, duration and rating as required.

The customer table stores the unique username, password and the user's date of birth.

The screen table has a uid for each screen, the screen number cannot uniquely identify a screen as each of the different cinemas have the same screen numbers e.g screen 1. The table stores the screen number, the number of seats and the cinema it is in. It references the cinema using the cinema's uid as a foreign key. This needs to exist for the booking system.

The showing table was necessary to add, to identify a screening of a particular movie at a particular time in a screen number in a cinema. This ensures that the booking system information is accurate for the booking table.

The booking table is the final table, it uses the booking number as the uid for the record. It records the customer username, the two different tickets, the showing, the seat numbers and the price.

# <mark style="background: #69E772;">LAB 2:</mark>

### <mark style="background: #69E772;">Part 1 - Paris:</mark>

<mark style="background: #69E772;">a. Adding a rank:</mark>
This added a rank to each participant in each event using the `RANK()` function. They were then sorted by result.

```plSQL
-- A. Adds a rank
select event_name, "result", participant_name, rank() 
over(
	partition by event_name
	order by "result" 
)
from paris;
```
![](https://i.imgur.com/dq6MYfS.png)

<mark style="background: #69E772;">b. Best 5 Irish athletes:</mark>
![](https://i.imgur.com/acCnbyX.png)

There were only 3 athletes listed as having "Ireland"

<mark style="background: #69E772;">c. Winner of Women's Marathon in Men's Race:</mark>
![](https://i.imgur.com/nCdqtr7.png)

Sifan Hassan would have been 68th in the Men's Marathon.

<mark style="background: #69E772;">d. Medal Table:</mark>
Created.

<mark style="background: #69E772;">e. Did the EU win more than the US</mark>
Yes. The US won 43, the EU won 66.

Austria ()
Belgium (1)
Bulgaria (1)
Croatia (1)
Cyprus (1)
Czechia (4)
Denmark (1)
Estonia
Finland (3)
France (9)
Germany (9)
Greece (5)
Hungary
Ireland (1)
Italy (11)
Latvia (1)
Lithuania
Luxembourg
Malta
Netherlands (8)
Poland (1)
Portugal (1)
Romania
Slovakia 
Slovenia (1)
Spain (5)
Sweden (2)

### <mark style="background: #69E772;">Part 2 - Stocks:</mark>

<mark style="background: #69E772;">b. 5 day moving average:</mark>
![](https://i.imgur.com/kuIoTpO.png)
(Sample image pictured above. )

A view called `movingAverage` shows a table where each row contains a stock's name, date, and the 5-day moving average of the `Close` price if it can be calculated. 

<mark style="background: #69E772;">c. Max and Min price of 2019</mark>
![](https://i.imgur.com/acbaIbu.png)

This query selects the max and min value from each table.

<mark style="background: #69E772;">d. Stock that gained the most in 2019</mark>
![](https://i.imgur.com/fj6Rflp.png)

Apple stock grew the most,  it grew by 188%. This query divides the closing stock by the opening stock and limits it to 2 decimals places.  Sorts the results by growth.

<mark style="background: #69E772;">e. Show if stock went up or down each day</mark>
![](https://i.imgur.com/BDGEyxb.png)

The query gets the stock of the day and day before it. It returns 1 if the stock is higher than the day before and 0 if the stock is not higher.

<mark style="background: #69E772;">f. How many days did Apple close with a gain:</mark>
![](https://i.imgur.com/rPsaDl4.png)

Apple closed with a gain on 146 days. The query counts all days where ``grow_or_not`` equalled 1.

<mark style="background: #69E772;">g. Monthly gain of each stock:</mark>
![](https://i.imgur.com/TpXJACO.png)

First you use a query to collate all the months. Then you use that to calculate the monthly gain or loss.
# <mark style="background: #69E772;">LAB 3:</mark>

### <mark style="background: #69E772;">Part 1 - Football:</mark>

<mark style="background: #69E772;">a. Logteam timestamps.</mark>

A function called `log_team_insertion()` is made that inserts the team name of a team being added to the TEAMS table, as well as the timestamp it was inserted at.

This is called by the trigger `after_insert_on_teams`, which is triggered for each row inserted to the TEAMS table.
![](https://i.imgur.com/snTC3HM.png)

<mark style="background: #69E772;">b. Insert into Euroleague if not there yet</mark>

An if statement was added to the previous trigger that checks if the inserted team name is in the EUROLEAGUE table and, if not, adds it in.

![](https://i.imgur.com/O5a0Ewv.png)

<mark style="background: #69E772;">c. Premier League matches must be two English teams, La Liga matches must be two Spanish teams</mark>

The function `check_team_countries()` selects the team names and checks that if the League is listed as Premier League, then both team countries are listed as "England" or it raises an exception. If it is not the Premier League, it checks if the league is "Spain" and that both teams are listed with "Spain" as the country name.

The function is triggered by the `before _insert_on_matches` trigger.

<mark style="background: #69E772;">d. + e. Make sure no team has more than four matches and add points for results.</mark>

The function for these two functionalities is `match_limit_and_update_points()`. It checks each team individually to count the amount of matches they have. If it is over four, it raises an exception. 

It has variables to count matches, points and differences.

It adds three points to the winning team, 1 point to a team that draws and no points to a team that loses. This is calculated from the goals scored.

The function is called by the trigger `before_insert_on_matches2`.

### <mark style="background: #69E772;">Part 2 - Hospital Patients</mark>

<mark style="background: #69E772;">a. Write a trigger to compute the BMI column (BMI = weight\*weight / height)</mark>

The function `bmi_insertion()` takes the patient's height and weight and uses the formula to calculate it. It then inserts that value as the new BMI. It does this before the insert on patient.

![](https://i.imgur.com/j1N7YDH.png)


<mark style="background: #69E772;">b. Write a trigger to store the previous data for a patient. Every time a patient is  UPDATED, save the old record in the table OLD_PATIENT_DATA.</mark>

The function `save_old_patient_data()` takes the patient's old data and stores it, useing the patientID and recordID as a compound primary key.. It does this after the insert on patient, which is done by updating.

![](https://i.imgur.com/UJi8UO1.png)

# <mark style="background: #69E772;">LAB 4:</mark>

### <mark style="background: #69E772;">Part 1- Gallery:</mark>

<mark style="background: #69E772;">1st Normal Form:</mark>
![](https://i.imgur.com/IdblSkx.png)

Primary key was added
<mark style="background: #69E772;">2nd Normal Form:</mark>
![](https://i.imgur.com/1cK1jp4.png)
![](https://i.imgur.com/c3G4ICF.png)

<mark style="background: #69E772;">3rd Normal Form:</mark>
![](https://i.imgur.com/VTMoU12.png)

### <mark style="background: #69E772;">Part 2 - Student Applications:</mark>

<mark style="background: #69E772;">1NF:</mark>
![](https://i.imgur.com/cc58Nd2.png)

Added a compound primary key that all the other variables are dependent on.

<mark style="background: #69E772;">2NF:</mark>
![](https://i.imgur.com/JxTa7Ii.png)

There are now 4 tables. The student table represents a unique student with a uid, and their name. 

The address table has a serial ID, as one student can have many addresses. The address table contains the ID of the student who lives in it, the street, the state, the zipcode and the application year. This means that there is only one piece of information per cell.

The prior school table contains the school's ID and the school's name. This means that the school name does not have to be manually written out each time.

The Applications table now contains the application number, student id, address id, application year, reference name, reference institution, reference statement, the prior school id and the GPA. It is more efficient to store the ID as opposed to a string. A lot of the duplicate data has been removed.

<mark style="background: #69E772;">3NF:</mark>
![](https://i.imgur.com/i55GJBT.png)
![](https://i.imgur.com/k1Zc7AX.png)
![](https://i.imgur.com/jMcLARF.png)


There are now seven tables. The Address, Student and Prior School tables remain unchanged.
# <mark style="background: #69E772;">LAB 5:</mark>

### <mark style="background: #69E772;">Exercise 1 - B-tree:</mark>

![](https://i.imgur.com/TzCheHX.png)
![](https://i.imgur.com/NxDCUTW.png)

![](https://i.imgur.com/7x0rtCS.png)
![](https://i.imgur.com/TMHToag.png)
![](https://i.imgur.com/5k1MAmt.png)


### <mark style="background: #69E772;">Exercise 2 - No rebalancing:</mark>

![](https://i.imgur.com/VhCEV61.png)
![](https://i.imgur.com/CBW3qms.png)
![](https://i.imgur.com/oWUMESw.png)
![](https://i.imgur.com/W5e9Am0.png)
![](https://i.imgur.com/16kWFaC.png)
![](https://i.imgur.com/Jrih2iu.png)


The main difference is how asymmetrical the tree is. It is heavily weighted to the right.

The main consequence is how many iterations are needed to reach the bottom, meaning it is inefficient to traverse.

### <mark style="background: #69E772;">Exercise 3: show and explain your computation in your document</mark>

![](https://i.imgur.com/PEjebmG.png)

![](https://i.imgur.com/FbaG4fP.png)

Difference between b-tree and simple tree:
2.53 / 2.94 = 0.86

Therefore, b-tree is 14% more efficient.

#### <mark style="background: #69E772;">Exercise 4: write the answers to each question in your document (no code is needed)</mark>

1. Total cost is 1.064 ms. Type of operation is regular Seq scan.
![](https://i.imgur.com/VWl6Gqy.png)

2. Total cost is 0.998 ms. Type of operation is Seq scan with a filter that removes unneeded rows. Cost is less than 
![](https://i.imgur.com/uKFxk0z.png)

3. Total cost is 1.256 ms. Type of operation is Seq scan with a filter
![](https://i.imgur.com/CwopCKG.png)