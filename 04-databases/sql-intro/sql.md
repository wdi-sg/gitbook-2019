## SQL: Structured Query Language

##Database Schema Design

For this lesson, how to design a complete database system is out of scope. We will discuss a few things here though.

The **schema** of the database is the set of create table commands that specify what the tables are and how they relate to each other. For our very simple database example, here is the schema:

```
                                                    Table "public.students"
 Column |         Type          |                       Modifiers
--------+-----------------------+-------------------------------------------------------
 id     | integer               | not null default nextval('students_id_seq'::regclass)
 name   | text                  |
 phone  | character varying(15) |
 email  | text                  |

```

## What is a Primary Key?

It denotes an attribute on a table that can uniquely identify the row.

### What does SERIAL Do?

SERIAL tells the database to automatically assign the next unused integer value to id whenever we insert into the database and do not specify id. In general, if you have a column that is set to SERIAL, it is a good idea to let the database assign the value for you.

## Data Types

Similar to how javascript has types of data, SQL defines types that can be stored in the DB. Here are some common ones:

* Serial
* Integer
* Numeric // Numbers are exact, no rounding error
* Float // Rounding error is possible, but operations are faster than Numeric
* Text, Varchar
* Timestamp
* Boolean (True or False)

You can set the storage size of some of these fields, but it could be a premature optimization that can cause problems later- you can't change the type while the DB is running.



### Data Types in Practice
- integer (sometimes numeric for non-integers)
- boolean
- timestamp
- text for everything else



### CREATE-ing a Table

This is an example of a students table.  (We will talk about the primary key soon.)
```sql
CREATE TABLE students (
    id SERIAL PRIMARY KEY,
    name TEXT,
    phone VARCHAR(15),
    email TEXT
);

```



### INSERT-ing Data

```sql
INSERT INTO students
(name, phone, email)
VALUES
('William Smith', '(415)555-5555', 'bill@example.com');

INSERT INTO students
(name, phone, email)
VALUES
('Bob Jones', '(415)555-5555', 'bob@example.com');

```



### SELECT-ing Data

```sql
SELECT * FROM students;

SELECT * FROM students WHERE name = 'Bob Jones';

SELECT id, name FROM students;
```



## UPDATE-ing Data

```sql
UPDATE students SET email='bobby@example.com' WHERE name = 'Bob Jones';
```



## DELETE-ing Data

```sql
DELETE from students WHERE name = 'Mary';
->DELETE 0
```

```sql
DELETE from students WHERE email = 'bobby@example.com';
->DELETE 1
```
Note: in pratice you will hardly ever delete anything, but mostly set a boolean 'valid' or something similar.



### DROP-ing a Table

```sql
DROP TABLE students;
```



### The WHERE clause
- can contain basically any conditional statement
- comparison ... > < <= >=
- and logical operators- AND OR NOT etc



### The ORDER BY clause
```
ORDER BY column_name, column_name ASC
```

ASC (ascending)
DESC (descending)




### Pairing Exercise

We'll use the w3schools page for doing our SQL: [https://www.w3schools.com/sql/trysql.asp?filename=trysql_asc](https://www.w3schools.com/sql/trysql.asp?filename=trysql_asc)

##### w3schools
This is an *implementation* of a SQL system that can use SQL language and store data. This is separate from the idea of a ORDBMS (postgres).

##### Instructions

Create a table for a movie database.

It will have a `title`, `description` and `rating`. `title` and `description` will be text, and rating will be an integer.

Make the CREATE TABLE command and execute it.

Once you're satisfied that the table is there, get rid of it using the DROP TABLE command.

###### Note:
Table creation usually uses a *serial* primary key: `id SERIAL PRIMARY KEY`

The SQL we are running for this exercise is different in this detail. `SERIAL` changes to `INTEGER`.

For the pairing exercise the primary key is declared with `id INTEGER PRIMARY KEY`

```sql
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    name TEXT,
    phone VARCHAR(15),
    email TEXT
);
```



### Inserting

And these insert statements:

```sql
INSERT INTO movies (title, description, rating) VALUES('Cars', 'a movie', 9);
INSERT INTO movies (title, description, rating) VALUES('Back to the Future', 'another movie', 9);
INSERT INTO movies (title, description, rating) VALUES('Dude Wheres My Car', 'probably a bad movie', 3);
INSERT INTO movies (title, description, rating) VALUES('Godfather', 'good movie', 10);
INSERT INTO movies (title, description, rating) VALUES('Mystic River', 'did not see it', 7);
INSERT INTO movies (title, description, rating) VALUES('Argo', 'a movie', 8);
INSERT INTO movies (title, description, rating) VALUES('Gigli', 'really bad movie', 1);
```

### Selecting

A select statement allows you to get data from the database. Postgres has a good [tutorial on select](http://www.postgresql.org/docs/7.3/static/tutorial-select.html). I'd recommend looking at the tutorial sometime after the lesson.



This will select all the attributes from the movies table unconditionally.  Make sure not to forget the ; at the end of each statement. In SQL, semi colons are required to terminate statements.

```sql
SELECT * FROM movies;
````

We may not want all attribues though.  Let's say instead we only care about the titles of the movie and the description.  Here is the query we'd use:

```sql
SELECT title, description FROM movies;
```


This will select the titles from movies table where the rating is greater than 4.

```sql
SELECT title FROM movies WHERE rating > 4;
```

You can also have more complex queries to get data.  The following query finds all the movies with a rating greater than 4 and with a title of Cars.

```sql
SELECT title FROM movies WHERE rating > 4 AND title = 'Cars';
```

SQL also supports an OR statement.  The following query will return any movie with a rating greater than 4, or any movies with the title Gigli.  In other words, if a movie called Gigli is found with a rating equal to 1, it will still be returned along with any movie with a rating greater than 4.

```sql
SELECT title FROM movies WHERE rating > 4 OR title = 'Gigli';
```

Let's say that we just want a list of the best movies of all time.  We can do a select statement that ensures ordering.  The DESC keyword tells it to order the rating in descending order. ASC is the default.

```sql
SELECT title, rating FROM movies ORDER BY rating DESC;
```

**Note:** If no order by clause is specified, the database does not give any guarantees on what order your data will be returned in. At times it may seem like data you are getting back is in sorted order, but make sure not to rely on that in your code. Only rely on a sort if you also have an ORDER BY clause.

We've gotten a list of movies back, but it's way too long for our uses.  Let's instead only get the top 5 movies that are returned using LIMIT:

```sql
SELECT title, rating FROM movies ORDER BY rating DESC LIMIT 5;
```

Write a query on the movie table to return the worst movie of all time.  There should be only 1 result returned. The result should include the title, description and rating of the movie.

### Updating

The update statement is defined [here](http://www.postgresql.org/docs/9.1/static/sql-update.html) in the postgres docs. It is used to change existing data in our database.

For example, if we do not think Gigli was actually that bad, and we want to change the rating to a 2, we can use an update statement:

```sql
UPDATE movies SET rating=2 WHERE title='Gigli';
```

### Deleting

Deleting works similarly to a select statement. Here are the [docs on delete](http://www.postgresql.org/docs/8.1/static/sql-delete.html)

The statement below deletes the Dude Wheres My Car row from the database:

```sql
DELETE FROM movies WHERE title='Dude Wheres My Car';
```

We could also use compound statements here:

```sql
DELETE FROM movies WHERE id < 9 AND rating = 2;
```

### Further

Continue with the w3schools sql exercises: [https://www.w3schools.com/sql/default.asp](https://www.w3schools.com/sql/default.asp)
