# Database Systems

## Objectives
* Understand the data storage landscape and where SQL RDBMS fit.
* Understand the added compexity of the DB system
* Connect to a PostgreSQL database using `psql`


## What is a database?

- It is a program that enforces structure on your data and allows a computer to quickly retreive data.
- A database should support CRUD operations


![https://image.slidesharecdn.com/GettoknowPostgreSQL-123559698726-phpapp02/95/get-to-know-postgresql-55-728.jpg?cb=1235575493](https://image.slidesharecdn.com/GettoknowPostgreSQL-123559698726-phpapp02/95/get-to-know-postgresql-55-728.jpg?cb=1235575493)


## Why Use a Database?

* Data is structured
* Databases are transactional
* Data retrevial is fast
* Has a system for remote access
* Has a system for backup


## Types of Databases

**RDBMS** (Relational Database Management System) The most common type of database today is a **relational database**.  Relational databases have tabular data with rows for each instance of data and columns for each attribut of that data. Tables may refer to one another. Relational databases typically use **SQL** (Structured Query Language).


###Brands of Relational Databases
* Postgres
* MySQL
* Oracle (Commercial Product with lots of features)
* Sybase
* Microsoft SQL Server
* SQLite (Good for mobile development/very small applications)

## How are databases used in the wild?
Every app needs to store data. The most popular data store by a wide margin is still something that runs SQL queries. These come in many different forms, but postgres is the DB we will be using in Rails and has been gaining popularity over mySql (it's main open source sql competitor) for the last 5 years. Other non-open source database systems include: Oracle, Microsoft SQL Server, Sybase, etc.

#### Data Storage:

##### Order of speed, reliability (least-to-most)
- memory (memcache, redis)
- noSQL (mongoDB, firebase)
- SQL (postgres)
- disk (jsonfile)

##### Order of sturcture, least-to-most
- disk (jsonfile, CSV)
- memory (memcache, redis)
- noSQL - (mongoDB, cassandra, firebase)
- SQL (postgres)


## PostgreSQL
Postgres is the DB system we will be working with.

If you installed Postgres.app you have access to psql from the elephant icon at the top of the screen:

Postgresql is an ORDBMS. Most ORDBMSs have these properties: (postgres included)

  - store data on disk
  - runs on the network
  - capable of interfacing with multiple services / servers at once
  - backup systems built-in
  - guarantees behavior for simultaneous-type transactions [ACID](https://en.wikipedia.org/wiki/ACID_(computer_science))
  - capable of running multiple copies of itself (replication)

* ![image](Postgres.png)

[Postgres Installation: OSX](/00-config-deployment/installfest/osx/readme.html#postgres)



#### Postgres.app default settings

|               |                               |
| ------------- |:-------------:                |
| host          | localhost                     |
| port          | 5432                          |
| user          | __your default system user__  |
| Database      | __same as username__          |
| password      | none                          |
| connection URL| postgresql://localhost        |



## PSQL
If you are using the command line:

* In your terminal, type `psql`.

**psql** is a command line tool to interact with postgres databases, by default it connects to the localhost database with the name of the current user

psql has some of it's own command which begin with `\`

List all of the available databases:

```
\list
```



List all of the available tables in the current database:

```
\dt
```

Check your connection information:

```
\conninfo
```

Your data is being stored on the disk. It is no longer a single file with just text characters inside. You won't be able to check your DB by looking inside the file for changes.

*But* you can see the file and where it is in the filesystem:

```
show data_directory;
```

There are lots of other commands which you can see with:

```
\?
```
Use `\q` to exit the help screen

Note that all psql commands start with `\`

## Creating a Database

Most database products have the notion of separate databases.  Lets create one for the lesson.
```
CREATE DATABASE testdb;
```

**ALL SQL COMMANDS MUST BE ENDED WITH A SEMICOLON IN THE PSQL SHELL**

Connect to a database
```
\connect testdb
```

Once we connect, our command prompt should look similar to this: `testdb=#`

List our tables in a database:
```
\dt
```

### Pairing Exercise

Open psql.
```shell
psql
```

Run the above code.

Create a table:

```sql
CREATE TABLE students (
    id SERIAL PRIMARY KEY,
    name TEXT,
    phone VARCHAR(15),
    email TEXT
);
```

Use \dt to verify that the table was created.

Use \d+ TABLE-NAME to see details about the table.

Copy and paste the SQL commands from the SQL language exercises.

Watch them run in `psql`.

Once you're satisfied that the table is there, get rid of it using the DROP TABLE command. Use \dt again to make sure that the table has been dropped.

#### Further

Repeat SQL from the previous exercise. See the output in `psql`.

