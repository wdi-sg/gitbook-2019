# MVC

MVC stands for Model View Controller

Each of these conceptual parts of the app will be broken up into different files.

This will give structure to our app and allow some code reuse.

We will be using this app as a reference:  [https://github.com/wdi-sg/mvc-template](https://github.com/wdi-sg/mvc-template)





## Pairing Exercise

Clone the MVC template repo.

Make sure `db.js` has the correct configuration for your DB (db name, user name).

Make sure you have a table called students:

```
CREATE TABLE IF NOT EXISTS students (
    id SERIAL PRIMARY KEY,
    name TEXT,
    email TEXT
);
```

Add some students into your DB, if you don't have any:

```
INSERT INTO students
(name, phone, email)
VALUES
('William Smith', '(415)555-5555', 'bill@example.com');

INSERT INTO students
(name, phone, email)
VALUES
('Bob Jones', '(415)555-5555', 'bob@example.com');
```

Add one route  to the routes file.

Add one method to the pokemon controller file.

Set the method as a callback of the route.

Create a new method in the pokemon model file.

Have it run a query against the `students` DB table:

```
SELECT * FROM students;
```

Now, in the controller create the callback that will be run when the query is finished. Pass it into the pokemon model method.

Execute the callback from the pokemon model method.

Pass the `queryResult.rows` back to the callback, and send it in response.send.

