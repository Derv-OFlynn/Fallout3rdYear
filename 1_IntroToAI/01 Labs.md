### <mark style="background: #69E7E4;">Lab 1:</mark>

Using Prolog first two weeks

SWI-Prolog

. is the line delimiter

Pulls from knowledge bases compiled using the "Consult" button

Words that start with capital letters are variables

Words that start with lowercase are called "atoms"

Declarative language

Have to restart every so often.

``:-`` means "implies"

Part of the CA is on Prolog

# <mark style="background: #69E7E4;">LAB 2 (Prolog Exercises)</mark>

2.1 Which of the following pairs of terms unify? Where relevant, give the variable instantiations that lead to successful unification.

1. bread  =  bread. <mark style="background: #69E7E4;">TRUE</mark>
2. ’Bread’  =  bread <mark style="background: #69E7E4;">FALSE</mark>
3. ’bread’  =  bread <mark style="background: #69E7E4;">TRUE</mark>
4. Bread  =  bread <mark style="background: #69E7E4;">Bread = bread.</mark>
5. bread  =  sausage <mark style="background: #69E7E4;">FALSE</mark>
6. food(bread)  =  bread <mark style="background: #69E7E4;">FALSE</mark>
7. food(bread)  =  X <mark style="background: #69E7E4;">X = food(bread)</mark>
8. food(X)  =  food(bread) <mark style="background: #69E7E4;">X = bread.</mark>
9. food(bread,X)  =  food(Y,sausage) <mark style="background: #69E7E4;">X = sausage,
Y = bread</mark>
10. food(bread,X,beer)  =  food(Y,sausage,X) <mark style="background: #69E7E4;">FALSE</mark>
11. food(bread,X,beer)  =  food(Y,kahuna_burger) <mark style="background: #69E7E4;">FALSE</mark>
12. food(X)  =  X <mark style="background: #69E7E4;">X = food(X).</mark>
13. meal(food(bread),drink(beer))  =  meal(X,Y) <mark style="background: #69E7E4;">X = food(bread),
Y = drink(beer).</mark>
14. meal(food(bread),X)  =  meal(X,drink(beer)) <mark style="background: #69E7E4;">FALSE</mark>

2.2 We are working with the following knowledge base:
   house_elf(dobby).  
   witch(hermione).  
   witch(’McGonagall’).  
   witch(rita_skeeter).  
   magic(X):-  house_elf(X).  
   magic(X):-  wizard(X).  
   magic(X):-  witch(X).

Which of the following queries are satisfied? Where relevant, give all the variable instantiations that lead to success.

1. ?-  magic(house_elf). <mark style="background: #69E7E4;">FALSE</mark>
2. ?-  wizard(harry). <mark style="background: #69E7E4;">TRUE</mark>
3. ?-  magic(wizard). <mark style="background: #69E7E4;">FALSE</mark>
4. ?-  magic(’McGonagall’). <mark style="background: #69E7E4;">FALSE</mark>
5. ?-  magic(Hermione). <mark style="background: #69E7E4;">Hermione = dobby</mark>

