## AJAX

We've covered an app from before unit 1, up to the beggining of unit 1.

Let's look back at the AJAX javascript from the *end* of unit 1:

Change the `script.js` file to include the code below:

```
// what to do when we recieve the request
var responseHandler = function() {
  console.log("response text", this.responseText);
  console.log("status text", this.statusText);
  console.log("status code", this.status);
};

// make a new request
var request = new XMLHttpRequest();

// listen for the request response
request.addEventListener("load", responseHandler);

// ready the system by calling open, and specifying the url
var url = "https://swapi.co/api/people/1";
request.open("GET", url);

// send the request
request.send();
```

Note that this is from the [gitbook](/gitbook-2019/02-js/browser-js/ajax.html)

##### Run the app again

[http://127.0.0.1:3000/hello](http://127.0.0.1:3000/hello)



### AJAX to our own express server

Change the `url` variable in `script.js` to something else:

```
var url = "http://127.0.0.1:3000/banana";
```

Run the app again. [http://127.0.0.1:3000/hello](http://127.0.0.1:3000/hello)

What happens?

##### Create a route that accepts this request:

```
app.get('/banana', (request, response) => {

  console.log('waffles');

  const data = {
    cucumber : "bacon",
    rice : "mango"
  };

  response.send(data);
});
```

#### pairing exercise

Run the above code.

##### further

Render the response of the request in the browser using DOM manipulation.

##### further

Install `pg` and make the `pool` variable. Hook the route `banana` up to a DB `SELECT` query. In the response of the request, send back the query result data.

##### further

Add likes:

Use one of your previous assignments that has user login.

A like is a join table from a resource (tweet, post, song, etc.) and a user.

Create the table for likes.

Create a route that will create a like.

- collect input from the user using an event in the DOM. (click event) the user clicks on a button or heart image
- get this input and put it in the AJAX request (the resouce id and the user id)
- use that part of the request to make your INSERT SQL query
- send the result back to the browser in the response
- when the response gets back to the bropwser, set the heart image to be filled in / change or give feedback in some way

#### further
Add comments (to songs, tweets, etc.) using AJAX.

#### further
Add editing of the resource using AJAX (PUT request)
