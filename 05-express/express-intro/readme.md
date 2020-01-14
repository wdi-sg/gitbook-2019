# First Express App with Routes

To create a web application using Node, we're going to import a web app server framework called Express. We can install this as a package using npm, then use it to create applications.

---

## Setting up a project
Create a new folder for use with the project using `mkdir node_calculator`, and cd into `cd node_calculator`

First we want to start a new project by going `npm init`. Follow the instructions, clicking `enter` through the statements. you many want to specify a version number, but most default options should be fine. It will also specify an initial file to use. The default is `index.js`, and this acts as the "entry point" into our app.

---

## Basic Express Setup

Before we do anything else, let's set up a basic Express app. We need to install our dependencies, create the index.js server file, and create an index for our homepage.

```bash
npm install express
touch index.js
```

**Note:** 

We've been running `npm install -g <package name>`to install the package globally. You'll want to reserve `-g` for packages that will be run in the command line.

---

### index.js

The following example shows how to get routes working in Node. A **route** is a combination of a URL pattern + HTTP Verb (get, post, put, delete). These verbs represent a method for the request.

Each route is called on our Express app, and takes a URL pattern and a callback function. The callback function gives us back the request (`request`) and response to send back to the client (`response`). Calling the `.send` function on the response sends a string back to the client.

```js
const express = require('express');
const app = express();

app.get('*', (request, response) => {
  response.send('hello brian');
});

app.listen(3000);
```

## Conditional Response

```
const express = require('express');
const app = express();

app.get('*', (request, response) => {
  response.send('hello brian');
});

app.listen(3000);
```

Get user input from the request path:
```
request.path
```

Respond based on what path is requested.
```
if( request.path == '/foo' ){
  response.send('yay');
}else{
  response.send('boo');
}
```

## Pairing Exercises:

#### Curl

Use `curl` to make a request to express from the terminal.

#### Request and Response Objects

See what else is in the request parameter by `console.log`ing it.

See what else is in the response parameter by `console.log`ing it.

#### Local Network
Find your IP address. Put the address into your browser and request your server through the local network. Ex. `168.4.3.1:3000/foo`

Change the address of your server with your pair.

Put your server address into the class slack channel.

#### Express Server on the Internet

Create an express server and put it on the internet using `ngrok`:

Run express:

```bash
node index.js
```

Open a new terminal window and start `ngrok` (what directory you are in doesn't matter)

```
cd my-ngrok-download-directory
./ngrok http 3000
```

Put your ngrok server address into the class slack channel.

#### HTML Response

Put HTML in `response.send`:

Paste this above the `app.get('*'` 

```
app.get('/papaya', (request, response) => {
  response.send('<html><body><h1>Hello</h1><a href="#">wow</a></body></html>');
});
```

What happens when you visit it using curl? `curl localhost:3000/papaya`

What happens when you visit it in the browser?

#### Ports

Create another directory and express server.

Listen on a different port.

Request from both servers.

Try to listen on the same port.

#### Paths

If the user requests bananas in the path, send back bananas.

If the user requests apples in the path, send back strawberries.

#### Further

If the user requests `/charizard`, send back information about charizard.
If the user requests `/pikachu`, send back information about pikachu.
If the user requests `/squirtle`, send back information about squirtle.


