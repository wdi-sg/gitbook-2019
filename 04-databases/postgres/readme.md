# PostgreSQL
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

