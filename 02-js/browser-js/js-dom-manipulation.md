# Intro to DOM

## DOM Manipulation

## Objectives
* Select elements from the DOM using selectors


## DOM Manipulation with JavaScript

**Review:** What is the DOM?

Open up the [MDN Website](https://developer.mozilla.org/en-US/)

Go to Developer Console. Look at DOM in *Elements*, then look at the DOM in *Console*. The object 'document' represents the DOM in JavaScript. We can change the DOM, i.e. the page, by changing the **document object**.

Review [DOM on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)



Now, inspect a few properties, for example:

```js
document.URL
document.head
document.links (what does it return?)
```



How to change the DOM? Select elements and manipulate them.

**Select by tag id:**

```js
var searchForm = document.querySelector("#home-q");
```

What's inside?

```js
searchForm.innerHTML;
```

Also, try `textContent` too! (you may also see this as `innerText`, but this is not supported by all browsers)



Change styling:

```js
searchForm.style.backgroundColor = "yellow";
searchForm.style.color = "red";
searchForm.style.height = "100px";
```



Properties can be a getter and setter. What does this mean?

**Select by class**

```js
var content_div = document.querySelectorAll(".center");
```

**Select by tag name**
```js
var allListElements = document.querySelector("li")
```



**Select using ANY CSS selectors**

Get elements by tag name or class is very unspecific. You can go after specific CSS selectors, just like you would in stylesheets:

```js
document.querySelectorAll("li");
document.querySelectorAll("li.nav-main-item");
document.querySelectorAll(".center > h1");
```



**Accessing and changing element attributes**

There are 2 ways to get and set attributes of a DOM element. You can access the properties directly or use use get/setAttribute methods. It's important that you know both exist, but generally accessing the properties directly is more consistent across browsers.

```html
<a id="stuff" href="http://www.yahoo.com">click me</a>
```

```js
//set using property
document.querySelector("#stuff").href = ' http://www.google.com';

//get using property
var href = document.querySelector("#stuff").href;

//get using getAttribute method
var href = document.querySelector("#stuff").getAttribute("href");

//set using setAttribute method
document.querySelector("#stuff").setAttribute("href","http://www.google.com")
```


## Compare and Contrast

Compare and contrast the following selectors. Why can't we use querySelector/querySelectorAll for everything?

* getElementById
* getElementsByClassName
* getElementsByTagName
* querySelector
* querySelectorAll



### Pairing Exercise (15 minutes)

* Open up your browser and go to the MDN Website.
* Repeat all of the exercies up to this point in the console.
- Create a set of styles for a header tag: `<h1>` that you create with javascript. (example: font-size, color, background color)
- Use `setTimeout` to apply those styles 4 seconds later. (add the class to the element)
