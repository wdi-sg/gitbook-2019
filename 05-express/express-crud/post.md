# CRUD in Express

We can now get things from the disk and display them as an HTML page to the user.

Next we want to take input from the user that will result in data being saved on our disk.

This is part of CRUD (Create, Read, Update, Destroy).

[Formal definition on wiki](http://en.wikipedia.org/wiki/Create,_read,_update_and_delete)



We will need several pieces to do this:
1. an HTML form
1. a route and response callback that takes that data
1. a place to store that data
1. and, an HTML page to show the user

First, let's talk about how to send data from the browser to the server.


### HTTP Post

#### Demo: How a user sends data over the internet: HTTP POST
Real-life recreation with paper. (One person pretends to be the backend)
- Prepare a request in the browser. verbs we are using: POST
- Send the request to a server
- server recieves the response
- reads the headers
- looks at the contents of the request
- constructs a response
- sends the response
- browser is waiting for the response
- Response has status and status code on the envelope.
- Deal with the server response
- If it's good, display the output to the user
- If it's bad, do nothing, or display an error to the user



Important Points:
- the parameters for the request are in the headers, the data itself is in the body of the request (inside the envelope)
- the point of a post request isn't always to save something, but a request where something is saved is almost always a post request



### How to make a POST request in the browser
- one of the main default behaviors of HTML in the browser is that `<a>` tags create `GET` requests and `form` tags create POST requests.

This behavior is always a default behavior given to us by the browser.

Given:
```
<form method="POST" action="/animals">
  Animal Name:
  <input type="text" name="name">
  <input type="submit" value="Submit">
</form>
```

When the submit button is clicked, this form will produce a POST request to the server.




#### RESTful Routing

RESTful routing is a scheme to structure your URLS that removes duplication, and looks clean. For each type of resource, you can specify a set of routes easily.

We don't need to rename the route animals, because express will separate things out depending on the HTTP method we use.

| **URL** | **HTTP Verb** |  **Action**| **Description** |
|------------|-------------|------------|----------------|
| /photos/         | GET       | index | Display a list of all photos |
| /photos/new      | GET       | new   | Display a form for creating a photo |
| /photos          | POST      | create | Accept a request for creating a photo |
| /photos/:id      | GET       | show | Display a page for a single photo |
| /photos/:id/edit | GET       | edit | Display a form for editing a specific photo |
| /photos/:id      | PATCH/PUT | update | Accept a request for new data for a specific photo |
| /photos/:id      | DELETE    | destroy | Accept a request to delete a specific photo |


[Read more on wiki](http://en.wikipedia.org/wiki/Representational_state_transfer)



## CRUD in action

To receive this data we need to create a `POST` route in express.




### Parsing Form Data

Parsing parameters from a form needs a built-in express middleware function.



**index.js**
```js
const express = require('express');
const app = express();

// tell your app to use the module
app.use(express.json());
app.use(express.urlencoded({
  extended: true
}));
```


Note that we set an attribute `extended` to `true` when telling our app to use the body parser. This attribute determines which library is used to parse data. Discussion on extended [here](https://expressjs.com/en/api.html#express.urlencoded).

Now, if we try to add this backend route, calling `req.body` should contain the form input.



**backend - express route**
```js
app.post('/animals', function(req, res) {
  //debug code (output request body)
  console.log(req.body);
  res.send(req.body);
});
```



### Pairing Exercise

create a new dir
```
mkdir post-exercise
```
cd into it
```
cd post-exercise
```
init npm
```
npm init
```
add express
```
npm install express
```
add jsonfile
```
npm install jsonfile
```
create an empty data.json file
```
echo {} >> data.json
```
start your app
```
nodemon index.js
```

use this express starter code in index.js:

```js
const jsonfile = require('jsonfile');
const express = require('express');
const app = express();

// tell your app to use the module
app.use(express.json());
app.use(express.urlencoded({
  extended: true
}));

app.post('/animals', function(request, response) {

  //debug code (output request body)
  console.log(request.body);


  // save the request body
  jsonfile.writeFile('data.json', request.body, (err) => {
    console.error(err)

    // now look inside your json file
    response.send(request.body);
  });
});

app.get('/', (request, response) => {
  // render a template form here
  response.send("hello world");
});

app.listen(3000, () => console.log('~~~ Tuning in to the waves of port 3000 ~~~'));
```

##### POST with CURL
Use a CURL command to make a POST request to your server

(We can use CURL to create the request, without having to construct anything else)
```
curl -d "monkey=banana&koala=eucalyptus" -X POST http://localhost:3000/animals
```

##### POST From the Browser

Write the html form to make the post request:

- Make a `GET` route (`app.get`) at `/myform`

- Send back this HTML form in the response:

```
<form method="POST" action="/animals">
  Animal Name:
  <input type="text" name="name">
  <input type="submit" value="Submit">
</form>
```
- try out your form

- watch the network tab to see the request go out.

##### Further

Create a route `add` that adds 2 numbers together.

`/add/3/4` will send 7 back in the response.

Save the numbers and the sum in the json file. The below object should represent one record in an array of records.

```js
{
  sum: 7,
  numA : 3,
  numB : 4
}
```

##### Further

Create a route that gets the sum results: `/results/0` will send back one of the above objects

##### Further
Create a route that gets the sum *of* results: `/addresults/0/1` will send back the sum of two results

##### Further
Create a route that gives the highest sum `/stats/highest`

##### Further
Create a route that gives the average sum `/stats/average`
