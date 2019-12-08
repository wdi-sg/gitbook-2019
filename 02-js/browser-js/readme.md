# Intro to Browser Javascript
![](from here: https://git.generalassemb.ly/ga-wdi-lessons/js-intro/blob/master/readme.md)


![](http://jce-il.github.io/ASOSMA/firefox-ios/general.jpg)

![](https://i.imgur.com/Qgz5eFD.png)

## Learning Objectives

- Describe the role Javascript plays alongside HTML and CSS
- Describe the DOM and it's implementation

## Framing (5 minutes / 0:05)

We've dabbled with HTML and CSS. There's a bit of interactivity we can program through CSS but not nearly enough! How can we start to add logic, data-handling and behaviors to our web apps? Enter Javascript.



#### If a web application or website were a building...

##### HTML: Structure and Content

HTML would be like the most stripped-down version of that building -- just the structure of the building, the building materials, and some content (maybe unfurnished offices, an empty classroom, a set of not-yet-operational bowling-lanes, etc).

##### CSS: Styling

CSS is responsible for the appearance of the building, adding granite floors, polished doors, wooden railings, etc. CSS styles the content of a website to look like more than just black text on a white background.

##### Javascript: Behavior & Functionality

Javascript might be like the building's elevator systems, ID-scanning & entry systems. Javascript handles interactivity and data.


## HTML vs JS

Look back at the pokedex html exercise. What kinds of interactions are enabled by HTML pages alone?

Javascript allows us to write code that is executed in response to user interaction

#### No Refreshes ➡ 👍 User Experience

## What is the DOM?

* Abstraction layer of what is actually happening on the browser screen ( model of the document )

* Alerts javascript to changes in the state of the HTML (events)

* Allows javascript programs to change the state of the HTML and CSS (document object)

* An "API" or interface to the browser screen from javascript

* Connects the networking part to the javascript part of the browser (so that we can connect that part to the screen)

#### document is just a variable:

Somewhere inside of chrome the devs have this code:

```js

var document = {};

// then some other stuff happens

// for example:
document.URL = 'mysite.com';
```

### Pairing Exercise: review the purpose of DOM and it's implementation

Open a sublime document. Write down some notes with your partner.

Open gmail, google docs, or google sheets. What interactions are enabled by HTML and what are not? How does it compare with the behaviors you see in `pokedex.html`?

Open up the [MDN Website](https://developer.mozilla.org/en-US/)

Go to Developer Console. Look at DOM in *Elements*, then look at the DOM in *Console*. The object 'document' represents the DOM in JavaScript. We can change the DOM, i.e. the page, by changing the **document object**.

Now, inspect a few properties, for example:

```js
document.URL
document.head
document.links (what does it return?)
```

Do the same for `window`.

