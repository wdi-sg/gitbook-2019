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

**app.js**

```javascript
const contacts = [
  { name: "Megatron", address: "Cybertron" },
  { name: "Some guy", address: "Some street" },
  { name: "Grace Hopper", address: "Arlington, Virginia" },
  { name: "Ching Shih", address: "The High Seas" },
  { name: "Slimer", address: "The Library" },
  { name: "Umbra", address: "The Void" },
  { name: "Hypatia", address: "The Neoplatonic school at Alexandria" },
  { name: "Matt Huntington", address: "Remote" },
  { name: "Ronald McDonald", address: "Casa del McDonalds" },
  { name: "Jem", address: "Starlight Music" }
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

* We will now be interacting with the DOM so wrap the code in jQuery's DOM on-load function.

* Create a container(table, with a header) that will house each name and address. Give it a class we can adjust later

```javascript

var buildTable = function(){
  const $infoTable = $('<table>').addClass('info-table')
  $infoTable.html(
    `<thead>
      <tr>
        <th>Name</th>
        <th>Location</th>
      </tr>
    </thead>`
  )
  var i=0;

  while(i<contacts.length){

    var contact = contacts[i];
    console.log(contact)
    i = i + 1;
  }

};

buildTable();
```

* Add in the table row and name cell, whose text comes from the array. Give it a class we can adjust later.

```javascript
const $infoRow = $('<tr>')
const $nameCell = $('<td>').addClass('name').text(contact.name)
```

And the address cell, whose text comes from the array. Give it a class we can adjust later.

```javascript
    const $addressCell = $('<td>').addClass('address').text(contact.address)
```

* Append the cells to the row
* Append the rows to the table


```js
$infoRow.append($nameCell, $addressCell)
$infoTable.append($infoRow)
```

Outside of the for loop (why?):

```js
  $('body').append($infoTable)
```
* Append the table to the body

Finished result

```javascript
$(() => {
  const buildTable = () => {
    const $infoTable = $('<table>').addClass('info-table')
    $infoTable.html(
      `<thead>
        <tr>
          <th>Name</th>
          <th>Location</th>
        </tr>
      </thead>`
    )
    for (let contact of contacts) {
      console.log(contact)
      const $infoRow = $('<tr>')
      const $nameCell = $('<td>').addClass('name').text(contact.name)
      const $addressCell = $('<td>').addClass('address').text(contact.address)
      $infoRow.append($nameCell, $addressCell)
      $infoTable.append($infoRow)
    }
    $('body').append($infoTable)
  }
})
```

### CSS


Give the info container some color, border, margin, padding

```css
@import url('https://fonts.googleapis.com/css?family=Poppins:400,700');


/***********************************
* GENERAL
************************************/
body {
  font-family: 'Poppins', sans-serif;
}

/***********************************
* TABLE
************************************/
.info-table {
  background-color: oldlace;
  margin: 1em auto;
  width: 70%;
  border-spacing: 0;
}

tr {
  boder-bottom: 2px solid grey;
}
td, th {
  border-bottom: 1px solid grey;
  padding: .5em;
}

th {
  font-size: 1.5em;
  background: moccasin;
}

tr:nth-child(even) {
  background: papayawhip;
}

tr:hover {
  background: blanchedalmond;
  color: steelblue;
}

.address {
  text-align: center;
}
```

### Adding data

* Write a function that will push new data in to the array.
* The function should take `name` and `address` as parameters
* The function should then run the 'buildTable' function


```javascript
const addData = (name, address) => {
  data.push({ name: name, address: address })
  buildTable()
}

$(() => {
    buildTable()
    addData('Karolin', 'NY')
});
```

The function 'doubles' the information. To fix this, we should clear out the old information before it populates. `$('body').empty()`

```javascript
const addData = (name, address) => {
  contacts.push({ name: name, address: address })
  $('body').empty()
  buildTable()
}

$(() => {
    buildTable()
    addData('Karolin', 'NY')
});
```

### Optional Activity

See if you can figure out how to create a removeData function that takes a name of a person you want to remove, removes them from the `data` array, then refreshes the rolodex.



### Basic Code:

**app.js**

```js
const contacts = [
  { name: "Megatron", address: "Cybertron" },
  { name: "Some guy", address: "Some street" },
  { name: "Grace Hopper", address: "Arlington, Virginia" },
  { name: "Ching Shih", address: "The High Seas" },
  { name: "Slimer", address: "The Library" },
  { name: "Umbra", address: "The Void" },
  { name: "Hypatia", address: "The Neoplatonic school at Alexandria" },
  { name: "Matt Huntington", address: "Remote" },
  { name: "Ronald McDonald", address: "Casa del McDonalds" },
  { name: "Jem", address: "Starlight Music" }
]


const buildTable = () => {
  const $infoTable = $('<table>').addClass('info-table')
  $infoTable.html(
    `<thead>
      <tr>
        <th>Name</th>
        <th>Location</th>
      </tr>
    </thead>`
  )
  for (let contact of contacts) {
    console.log(contact)

    const $infoRow = $('<tr>')
    const $nameCell = $('<td>').addClass('name').text(contact.name)
    const $addressCell = $('<td>').addClass('address').text(contact.address)
    $infoRow.append($nameCell, $addressCell)
    $infoTable.append($infoRow)

  }
  $('body').append($infoTable)
}

const addData = (name, address) => {
  contacts.push({ name: name, address: address })
  $('body').empty()
  buildTable()
}

$(() => {
  buildTable()
  addData('Karolin', 'NY')
})
```
