# The Internet

### Context

Before we can describe the internet from a javascript perspective, we have to talk about what the internet is.

- network of computers
- sending things across the network
- just computers talking to computers



#### Objectives
- Learn about how things get transported over the internet
- Learn about the pricipal of request response
- See some different responses after requesting things over the internet
- Implement a request and deal with the response in javascript



## Demo: How to send things over the internet:
Real-life recreation with paper. (One person pretends to be the backend)
- Prepare a request in the browser
- Send the request to a server
- Wait for the response
- Response has status and status code on the envelope.
- Deal with the server response
- If it's good, display the output to the user
- If it's bad, do nothing, or display an error to the user



### Demo: Actually Getting Things
1. Open your browser
1. Type in google.com in the address bar
1. Hit enter (You request the page from google.com)
1. Your browser recieves the response and displays the result

#### Dev Console Network Tab
- clicking on the network tab, you will be able to see all other requests the browser makes when loading a page.



## Getting web pages on "the web"

### Naming of Resources and Categorization of Data

- Each thing we request is a resource
- URLs are a specficication for the location of a resource
- We format the request for the resources in a particular syntax
- We can request web pages through the browser
- We can request JSON through javascript
- (We can request either through either)
- URLs are formatted similarly to file paths
- There is a root path, ans then a set of resources
- Each web dev chooses a way to format the order of a URL



#### The Web Is a Big Collection of HTML Pages on the Internet

The World Wide Web, or "Web" for short, is a massive collection of digital pages: that large software subset of the Internet dedicated to broadcasting content in the form of HTML pages. The Web is viewed by using free software called web browsers. Born in 1989, the Web is based on hypertext transfer protocol, the language which allows you and me to "jump" (hyperlink) to any other public web page. There are over 65 billion public web pages on the Web today."

- Taken from [About Tech](http://netforbeginners.about.com/od/i/f/What-Is-The-Internet.htm)




#### Elements of a URL

URL stands for Uniform Resource Locator, and it's just a string of text characters used by Web browsers, email clients and other software to format the contents of an internet request message.

Let's breakdown the contents of a URL:

> Note. Draw the following on the board

```
    http://www.example.org/hello/world/foo.html?foo=bar&baz=bat#footer
    \___/  \_____________/ \__________________/ \_____________/ \____/
  protocol  host/domain name        path         querystring     hash/fragment
```


```
    http://www.example.org:3000/hello/world/foo.html?foo=bar&baz=bat#footer
    \__/  \_____________/ \__/\__________________/ \_____________/ \____/
protocol|host/domain name|port|      path         | querystring   | hash/fragment
```




Element | About
------|--------
protocol | the most popular application protocol used on the world wide web is HTTP. Other familiar types of application protocols include FTP, SSH, GIT, FILE, HTTPS
host/domain name | the host or domain name is looked up in DNS to find the IP address of the host - the server that's providing the resource. This may include a subdomain, which in it's simplest sense is like a folder on the server. www is actually a subdomain and is often used by default on servers, allowing you to omit it in the URL sometimes.
path | web servers can organise resources into what is effectively files in directories; the path indicates to the server which file from which directory the client wants
querystring | the client can pass parameters to the server through the querystring (in a GET request method); the server can then use these to customise the response - such as values to filter a search result
hash/fragment | the URI fragment is generally used by the client to identify some portion of the content in the response; interestingly, a broken hash will not break the whole link - it isn't the case for the previous elements

<br>
_The Schema above is from [Tuts +](http://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)_


## HTTP
- a **structured** protocol for sending and recieving HTML (or other data)
- protocol, as in the military, a set of conventions for behavior given a set of circumstances
- how to deal with scenarios that go wrong: https://swapi.co/lkjlkjlkj
- we are using `GET` method to **get** things. We'll learn others in Unit 2.
- HTTP status codes: [https://en.wikipedia.org/wiki/List_of_HTTP_status_codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)



#### Anti-demo: Not getting things
1. Open your browser
1. Type in google.com/lkjlkjlkjljlkjl in the address bar
1. Hit enter (You request the page from google.com)
1. Your browser recieves the response and displays the result


### Requests from an HTML file

Given the HTML below, what elements are involved in making an HTTP request?

```HTML
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>


    <p>
      <a href="https://www.google.com">google.com</a>
    </p>


    <p>
      <img src="https://source.unsplash.com/random"/>
    </p>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy" crossorigin="anonymous"></script>
  </body>
</html>
```


### Pairing Exercises

##### Dev Console
- open a new tab
- open the dev console
- click to the network tab
- if there are any requests, clear them with the clear button
- open up [generealassemb.ly](http://www.generalassemb.ly)
- watch the requests happen inside the console
- note the order of the requests
- click on a couple of the indiuvidual requests to see the details-
  - detail tab: General -> Request URL, Request Headers, etc.
  - click to the `Preview` tab to see a preview of the request response

##### Your Own Page
- create an index.html page
- create some elements that create requests - `a` `img` `link` `script`
- set each of these to real assets that exist on the internet:
  - set `a` to google.com or similar
  - set `img` to an image found on google image search
  - set `link` to the bootstrap library
  - set `script` to the bootstrap javascript library
- watch these requests in the network tab
- change your html code so that these requests *will not* work.
- reload the page to see what happens

##### Javascript

1. write a function that adds an img to the page (with a src from above). Open the dev tools so that the console and the network tab is visible. In the console, call your function.

2. Create an array of image urls. Use a `setInterval` to add a new `img` tag to the page every 2 seconds with a different source from the array. Watch the network tab of the browser.

3. Add some non-valid image urls to your array. Run your code again and watch the metwork tab.


