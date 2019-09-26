# Flexbox Column Layout

Prequisite: [Flexbox Froggy](https://flexboxfroggy.com/)

From: [https://dev.to/drews256/ridiculously-easy-row-and-column-layouts-with-flexbox-1k01](https://dev.to/drews256/ridiculously-easy-row-and-column-layouts-with-flexbox-1k01)

### html

```
<div class="some-page-wrapper">
  <div class="row">
    <div class="column">
      <div class="blue-column">
        Some Text in Column One
      </div>
    </div>
    <div class="column">
      <div class="green-column">
        Some Text in Column Two
      </div>
    </div>
  </div>
</div>
```

### css
```
.some-page-wrapper {
  margin: 15px;
  background-color: red;
}

.row {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 100%;
}

.column {
  display: flex;
  flex-direction: column;
  flex-basis: 100%;
  flex-grow: 1;
}

.blue-column {
  background-color: blue;
  height: 100px;
}

.green-column {
  background-color: green;
  height: 100px;
}
```

##### Double size column:
```
.double-column {
  display: flex;
  flex-direction: column;
  flex-basis: 100%;
  flex-grow: 2;
}
```

##### Responsive:
```
@media (min-width: 800px) {
  .column {
    flex-grow: 1
  }

  .double-column {
    flex-grow: 2
  }
}
```

References: [CSS Tricks' guide to flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

### Pairing Exercise
Repeat the above code.

### Further
Make a 3rd div with content inside. Create a 3 column layout above 1000 pixels.

### Further
When in the widest configuration, the columns run from right to left.

### Further
Create a [sticky footer](https://philipwalton.github.io/solved-by-flexbox/demos/sticky-footer/) for your page.
