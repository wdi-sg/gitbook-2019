# AJAX

### Requests From Javascript

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
request.open("GET", "https://swapi.co/api/people/1");

// send the request
request.send();
```


Change it from a string type into a javascript object

```
var responseHandler = function() {
  console.log("response text", this.responseText);
  var response = JSON.parse( this.responseText );
  console.log( response );
};
```



- Note: `new` keyword creates a new `XMLHttpRequest`
- Note: `JSON` is built-in functionality that deals with JSON.
- Note: I can also visit https://swapi.co/api/people/1 in the browser.

From: [MDN](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest)
From: [Moar MDN](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Synchronous_and_Asynchronous_Requests)


- why do we need to use callbacks?
- we don't want to freeze the user experience while the user loads a slow request


### Handling Errors

#### Request "error" event and handlers
```
var requestFailed = function(){
  console.log("response text", this.responseText);
  console.log("status text", this.statusText);
  console.log("status code", this.status);
};

request.addEventListener("error", requestFailed);
```


### Pairing Exercises

##### See What Data You Are Getting
- go to the URL you are making a reuqest to (the one in the code above)
- what happens when you change the URL to something else? i.e. `/api/people/2` or `/api/films/1`

##### AJAX

Create a new `index.html` file with an empty `body` tag.
Create an empty `script.js` file

Copy this code:
```
// make a new request
var request = new XMLHttpRequest();

// ready the system by calling open, and specifying the url
request.open("GET", "https://swapi.co/api/people/1");
```

Click the network tab and find your ajax request. Click it to see the response body.
There won't be any request yet! You need to send the request:

```
request.send();
```

Click the network tab and find your ajax request. Click it to see the response body.

Add the callback that deals with the response:

```
var responseHandler = function() {
  console.log("response text", this.responseText);
  console.log("status text", this.statusText);
  console.log("status code", this.status);
};
```

Listen for it:

```
// listen for the request response
request.addEventListener("load", responseHandler);
```

Click the network tab and find your ajax request. Click it to see the response body. Check the callback console.log is it the same as what you saee in the network tab?

#### JSON

You want to be able to get *data* from the response.

Use the `JSON.parse` so that you can create variables from the object for name and height. Inside the callback write this console.
```
console.log("This person's name is: "+name+" and their height is: "+height);
```


#### Further:
- Use this html: `<input id="url" type="text"/><button id="submit">submit</button>` to get user input
- Use this javascript to get the user input:
```
var doSubmit = function(event){
  var input = document.querySelector('#url');
  var url = input.value;
};

document.querySelector('#submit').addEventListener('click', doSubmit);
```
- set the `url` variable as the variable of the request
- check out the swapi [documentation](https://swapi.co/documentation)
- input a few more urls and send a request. See the response in the console.

#### Further 2:
- put in a url string that doesn't make any sense, a completely invalid url, i.e. "83du4j4u".
- use an `error` event handler callback to alert the user when an error occurs.

#### Further 3

Check out this list to see where you can make other requests: [https://github.com/toddmotto/public-apis
](https://github.com/toddmotto/public-apis
)

(You can't make a request to anywhere from browser javascript)
