# <mark style="background: #69E772;">LAB 1 - ERDs:</mark>

### **Exercise 1 (short question on DB modelling)**  
**A database contains a list of toys, all of them identified by a name, a price, a unique ID. However, toys are different, and each toy could have specific attributes that only that toy has. For instance, the toy car has 2 attributes specific to a car: engine_size, petrol_or_diesel. The toy teddy has two other specific attributes: material and age (and, of course, teddy does not have the engine_size and petrol_or_diesel attributes, and the toy car does not have the material and age attributes) and so on... How would you store this information in a database? Explain and justify your solution. Consider all the potential aspects of the solution (easy to use and maintain, performance, storage efficiency, what if some new attributes are added?). You might also search the web for the problem.**  

**Implement your solution in Postgres and insert some data to demonstrate your solution.**

Toy (super class)
name
price 
uid

Car (subclass of toy):
engine_size
petrol_or_diesel
uid

Teddy_Bear (subclass of Toy):
material
age
uid

![](https://i.imgur.com/lPCWWPe.png)

```SQL
drop table if exists car;

drop table if exists teddy;

drop table if exists toy;

create table toy (uid VARCHAR(20) primary KEY UNIQUE NOT NULL, price VARCHAR(10), name VARCHAR(20));

create table teddy (uid VARCHAR(20) primary KEY UNIQUE NOT NULL, age VARCHAR(10), material VARCHAR(20));

create table car (uid VARCHAR(20) primary KEY UNIQUE NOT NULL, engine_size VARCHAR(10), petrol_or_diesel VARCHAR(20));

  

INSERT INTO toy VALUES ('860', '10', 'Bear'), ('310', '1.8', 'petrol');

INSERT INTO teddy VALUES ('860', '14', 'Felt');

INSERT INTO car VALUES ();  

select * from toy, teddy WHERE toy.uid = teddy.uid;
```

Exercise 2 – From ER diagram to relational model.
You need to model the relationship between two entities E1 and E2. Suppose the key of  E1 is the attribute K1 and the key of E2 is attribute K2. You can ignore the other entities attributes.  
	a. Chose 3 of the following 6 situations and show how they can be modelled using a relational model (tables and keys) and how it can be implemented in Postgres (using create table statements).

![](https://i.imgur.com/OFgpdlC.png)

a. E<sub>1</sub> must exist, only one (PK), E2 can exist and multiple can

# <mark style="background: #69E772;">LAB 2:</mark>

PART 1 // Paris 2024 Athletics Results  
The file “Paris 2024 Result.csv” contains the results of all the finals of the recent Olympics Games in Paris for the sport athletics, form 100meters to marathon. The columns of the csv are as follows:  
- Date: the date of the final in the format “2024-08-07”  
- Event Name: the name of the event (like “High Jump”)  
- Gender: gender of the athlete or of the team (X mean a “mixed” team competition, like the 4x400 meter mixed relay)  
- Participant name: name of the athlete  
- Participant type: can be “Person” or “Team”  
- Participant Country Code: unique code for the country (like “IRL” for Ireland)  
- Participant Country: Name of the country (like “Ireland”)  
- Result: the result obtained by the athlete in the event. It is represented by a decimal number. For competitions against time (= all the running events), the result is expressed in seconds, for competition based on distance (like “long jump” or “discus throw”) the result is expressed in meters.  
- Result type: either “Distance” or “Time”, according to the type of event  

For instance, for the 100 meters (men), these are the rows in the CSV:
![](https://i.imgur.com/G3rCrxM.png)

a. Add a rank for each participant in each event (hint: use the rank window  
functions as seen in class). Use the right ranking function (RANK or  
DENSE_RANK ?). Save your query in a view, since you will need to re-use the  
output of the query for the other questions

```SQL
select event_name, "result", participant_name, gender, rank()
over(
	partition by event_name, gender
	order by "result"
)
from paris;
```

b. Identify the best 5 Irish athletes based on their ranking
```SQL
select participant_name, "result", participant_country, event_name
from paris
where participant_country = 'Ireland'
order by "result"
limit 5;
```

c. If the winner of the Women’s Marathon would have competed in the Men’s Marathon, what her position in the ranking would have been?

```SQL
select participant_name, "result", event_name
from paris
where event_name = 'Women''s Marathon' or event_name = 'Men''s Marathon'
order by "result";
```