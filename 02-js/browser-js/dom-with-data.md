# DOM with data

Here is a rolodex with people's names and addresses:

![](https://i.imgur.com/PihqmAi.png)

We would like to run a function that will populate our page with names and addresses from an **array of objects**

## Set Up

Set up HTML:

1. add html boilerplate
1. add `script.js` script src
1. add `style.css` with a link, rel is stylesheet
1. add a `div` with a class `container`

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
    <head>
        <meta charset="utf-8">
        <title></title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
      <div class="container">

      </div>
      <script src="script.js" charset="utf-8"></script>
    </body>
</html>
```

### Data

* Add the **array of objects**


```javascript
var contacts = [
  { name: "Megatron", address: "Cybertron", coWorker : true },
  { name: "Some guy", address: "Some street", coWorker : false },
  { name: "Grace Hopper", address: "Arlington, Virginia", coWorker : false },
  { name: "Ching Shih", address: "The High Seas", coWorker : false },
  { name: "Slimer", address: "The Library", coWorker : true },
  { name: "Umbra", address: "The Void", coWorker : false },
  { name: "Hypatia", address: "The Neoplatonic school at Alexandria", coWorker : false },
  { name: "Matt Huntington", address: "Remote", coWorker : false },
  { name: "Ronald McDonald", address: "Casa del McDonalds", coWorker : true },
  { name: "Jem", address: "Starlight Music", coWorker : true }
];
```

What we want to do is **populate** our page with data from the array. If, in the future, we change the data in the array, the page can be **re-populated**.

* Write a loop that iterates over the array

```javascript
var i=0;

while(i<contacts.length){

  var contact = contacts[i];
	console.log(contact)
  i = i + 1;
}
```

* Create a container(div) that will house each name and address. Give it a class we can adjust later

```javascript

var buildTable = function(contacts){
  var info = document.createElement('ul');

  var i=0;

  while(i<contacts.length){

    var contact = contacts[i];
    console.log(contact)
    i = i + 1;
  }

};

buildTable(contacts);
```

* Add in the row and name, whose text comes from the array. Give it a class we can adjust later.

```javascript
var infoRow = document.createElement('li');
var nameParagraph = document.createElement('p');
nameParagraph.classList.add('name');
nameParagraph.innerText = contact.name;
```

And the address, whose text comes from the array. Give it a class we can adjust later.

```javascript
var addressParagraph = document.createElement('p')
addressParagraph.classList.add('address');
addresssParagraph.innerText = contact.address;
```

* Append the `p`'s to the row
* Append the rows to the main div


```js
infoRow.appendChild(name, address);
info.appendChild(infoRow);
```

Outside of the for loop (why?):

```js
document.body.appendChild(info);
```
* Append to the body

Finished result

```javascript
var buildTable = function(contacts){
  var info = document.createElement('ul');

  var i=0;

  while(i<contacts.length){

    var contact = contacts[i];
    console.log(contact)


    var infoRow = document.createElement('li');
    var nameParagraph = document.createElement('p');
    nameParagraph.classList.add('name');
    nameParagraph.innerText = contact.name;

    var addressParagraph = document.createElement('p')
    addressParagraph.classList.add('address');
    addresssParagraph.innerText = contact.address;

    infoRow.appendChild(nameParagraph, addressParagraph);
    info.appendChild(infoRow);

    i = i + 1;
  }

  document.body.appendChild(info);

};

buildTable(contacts);
```

### Adding data

* Write a function that will push new data in to the array.
* The function should take `name` and `address` as parameters
* The function should then run the 'buildTable' function


```javascript
var addData = function(name, address, coWorker) {
  contacts.push({ name: name, address: address, coWorker:coWorker })
  buildTable(contacts)
};

buildTable(contacts);
addData('Karolin', 'NY', true);
```

The function 'doubles' the information. To fix this, we should clear out the old information before it populates. `$('body').empty()`

```javascript
var addData = (name, address) {
  contacts.push({ name: name, address: address, coWorker:coWorker })
  document.body.innerHTML = "";
  buildTable(contacts);
}

buildTable(contacts);
addData('Karolin', 'NY', true);
```

### Pairing Exercise

Run the above code.

### Further

Make the code intertactive. When the page loads, create the table.

Add a button and three inputs:


```html
<input id="name"/>
<input id="address"/>
<input id="coworker"/>
<button id="add">click to add</button>
```

The user will type ion the three inputs.

When they click the button, get the data from the inputs and put it into the contacts array.

### Further

See if you can figure out how to create a removeData function that takes a name of a person you want to remove, removes them from the `data` array, then refreshes the rolodex.

### Further
Start with an empty page.

When the page loads, create the starting elements in the DOM and add them to the page.
