### ERDs

ERDs are diagrams that model the relationships between data.

**Car Sales**
Cars have owners
Cars belong to brands
Cars have salespeople
Sales people have many customers (who have bought a car)

![](https://github.com/wdi-sg/gitbook-2018/blob/master/images/cars-erd.jpg?raw=true)

**Primary School**
Teachers have many students
Students have one teacher
Students have many books

![](https://github.com/wdi-sg/gitbook-2018/blob/master/images/student-erd.jpg?raw=true)

**Twitter**
User has many tweets
Tweets has one video

![](https://github.com/wdi-sg/gitbook-2018/blob/master/images/tweets-erd.jpg?raw=true)

#### Exercise

- Pick one or more of the following analyze what it primarily does & try to draw the tables & relationships. Don't try to model every single piece of data within the app. Start with the most important models and add on from there.

  - Facebook
  - 99.co
  - Github
  - Carousell
  - AirBnB
  - Medium
  
  Hint: If you're not sure how to make a given table or store a piece of data, write in, with dummy data, all the columns of a single record / row.

#### 1
An ERD diagram, using crow's foot notation, of whatever app you choose.  For example:


<p align="center">
  <img src ="https://www.edrawsoft.com/images/examples/entity-relationship-diagram.png">
</p>

> Note: this example has "Items" as placeholders for the attributes.

**Warning: DO NOT try to implement the entire app. That will be way too big. Start with the major features. Then move on to the next part (2).** If you get done with the below, come back and add to the ERD.

#### 2
Write the `tables.sql` file for this app. 

(If you found out you made a mistake in your table creation when you run your seed file, or when you are working on your own at all, make sure to coordinate with your partner to fix these errors.)

#### 3
Write a `seed.sql` for the first row or two in every table.

#### 4
Write the sql SELECT queries that gets every major relationship in the app in a `queries.sql` file. (Make sure you have enough dummy data to get at least one row.)

For example, for Facebook, write an sql SELECT to get:

* my friends on Facebook
* photos I'm tagged in
* every user in a Facebook group
* etc.

## Additional Resources

- [crows foot notation cheat sheet](http://www.vivekmchawla.com/content/images/2013/Dec/ERD_Relationship_Symbols_Quick_Reference-1.png)

