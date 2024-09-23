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