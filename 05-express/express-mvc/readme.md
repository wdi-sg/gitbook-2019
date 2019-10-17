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

Add one route  to the routes file. `/students`

Add one method to the pokemon controller file for this route.

Set the method as a callback of the route.

Create a new method in the pokemon model file.

Have it run a query against the `students` DB table:

```
SELECT * FROM students;
```

Now, in the controller create the callback that will be run when the query is finished. Pass it into the pokemon model method.

Execute the callback from the pokemon model method.

Pass the `queryResult.rows` back to the callback, and send it in response.send.


#### Further

In the above exercise, you added methods to the files that already exist.

This is not how you would normally do it, because you will have **one** controller and model *for each* type of data. (most likely one for each table, excluding some join tables)

Now add a new model, `classes`.

Add a get route to render a form to create a single class (`GET /classes/new`)

Add a `classes` model.

Add a model method to take in the `POST` request this form creates.


#### Further

Create a relationship between student and classes. Student has many classes.

Create a `student_id` foreign key inside of the `classes` table.

Add the page (route and controller) for a single student (`GET /student/:id`).

Add the model for the single student. The model should execute this query: (`SELECT * FROM students WHERE id=`);

On the student page, list all of that student's classes.

You can do this by composing two queries together for student with the query for classes:

```js
// controller for /students/:id
let studentControllerCallback = (request, response) => {

  db.students.get(1, (student)=>{
    //  inside the callback, now that you have the student
    //  get the list of classes

    let student_id = student.id;

    db.classes.getByStudent(student_id, (classes)=>{

      const data = {
        studentKey : student,
        classesKey : classes
      };

      response.render('student' data );


    });

  });

};
```

#### Further

Fill in the rest of the `restful` routes for students and classes.

Make students files instead of pokemon.

