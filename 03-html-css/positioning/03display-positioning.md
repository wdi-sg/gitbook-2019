# Display

Display has to do with the flow of a document and what elements take up what space.

Elements are processed like in a text document, they flow from the top left to the right and then towards the bottom line by line.

Different elements have different kinds of properties for how much space they will take up and how.

Certain elements always have certain default display properties:


| element | display |
|--- | --- |
| p | block |
| div | block |
| h tag (h1) | block |
| input | inline |
| img | inline |
| a | inline |
| span | inline |

## Taking Up Space using Display

![https://media.giphy.com/media/13yeYZJuM4LpjW/giphy.gif](https://media.giphy.com/media/13yeYZJuM4LpjW/giphy.gif)

From here: [https://stackoverflow.com/questions/9189810/css-display-inline-vs-inline-block](https://stackoverflow.com/questions/9189810/css-display-inline-vs-inline-block)

### Inline elements:

  - respect left & right margins and padding, but not top & bottom
  - cannot have a width and height set
  - allow other elements to sit to their left and right.
  - you don't usually style these elements heavily with box model styles

  Example: text styling
```css
.highlight{
  background-color:yellow;
  padding:3px;
}
```

```html
<p>
  To operate your life vest <span class="highlight">pull on the red strap</span>. If it does not inflate, blow on the attached tube.
</p>
```

### Block elements:

- respect left & right margins and padding & top & bottom
- force a line break after the block element
- acquires full-width if width not defined

Example: Layout rows:
```css
.row1{
  background-color:yellow;
}
.row2{
  background-color:blue;
}
.row3{
  background-color:red;
}
```

```html
<div class="row1">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer luctus a nulla in efficitur.
</div>
<div class="row2">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer luctus a nulla in efficitur.
</div>
<div class="row3">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer luctus a nulla in efficitur.
</div>
```

### Inline-block elements:

    - allow other elements to sit to their left and right
    - respect top & bottom margins and padding
    - respect height and width
    - can create a line break if element is longer than width (doesn't break in the middle of the element- like a block)


Example: Nav Bar Layout:
```css
.nav-button{
  display:inline-block;
  margin:0;
  padding:5px;
  width: 200px;
}
.nav1{
  background-color:yellow;
}
.nav2{
  background-color:blue;
}
.nav3{
  background-color:red;
}
```

```html
<div class="nav-button nav1">
  About
</div>
<div class="nav-button nav2">
  Sign Up
</div>
<div class="nav-button nav3">
  Login
</div>
```


### Pairing Exercises

Create an empty html file and css file.

You will be creating a bunch of divs:

```
<div class="box-demo">box demo</div>
```

Set a background-color and border on each div so you can see it's behavior.
```
.box-demo{
  background-color:yellow;
  border:1px solid black;
}
```

##### Box model
Change the size and area the box takes up by setting the `padding` `border` and margin of the boxes.

Make the padding visible by putting one box inside of the other:

```HTML
<div>
  <p>hello</p>
</div>
```

```
div{
  padding:10px;
  background-color:yellow;
}

p{
  margin:10px;
  padding:10px;
  background-color:blue;
}
```

Use the chrome dev tools to inspect the size of the boxes.

Use the chrome dev tools to manipulate the amount of border, padding and margin.

##### Display Inline

Create a series of divs as above and add the class `inline-demo`. In your CSS file set these divs to display inline.

Open the chrome console and see these elements behave weird if you put too much padding and margin on them (specifically top and bottom margin /padding)

Resize the width of the screen and see how the boxes flow around the screen and wrap.

How do these divs wrap when you have a long string inside with no spaces? i.e.: `983749012739407129034719023740912837017230971209347129038740192837490128739047182390871290387401923874091287340981723498`

##### Display Inline Block

Create a series of divs as above and add the class `inline-block-demo`. In your CSS file set these divs to display inline-block.

Resize the width of the screen and see how the boxes flow around the screen.

What happens when you put these elements around other inline elements?

```
====== inline element ======
====== inline element ======
====== inline element ======
=== inline-block element ===
=== inline-block element ===
====== inline element ======
=== inline-block element ===
```

##### Display Block
Create a series of divs as above and add the class `block-demo`. In your CSS file set these divs to display block.

Resize the width of the screen and see how the boxes flow around the screen.

In the chrome console, explicitly set the width of the block elements to less than 100%. See what happens when you make them narrower and narrower.

What happens when you put these narrow elements around other kinds of display elements?

```
====== inline element ======
====== inline element ======
====== block  element ======
====== block  element ======
====== block  element ======
====== inline element ======
=== inline-block element ===
=== inline-block element ===
====== inline element ======
=== inline-block element ===
```

