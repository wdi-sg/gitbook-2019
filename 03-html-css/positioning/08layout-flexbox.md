# Flexbox Column Layout

Prequisite: [Flexbox Froggy](https://flexboxfroggy.com/)

From: [https://dev.to/drews256/ridiculously-easy-row-and-column-layouts-with-flexbox-1k01](https://dev.to/drews256/ridiculously-easy-row-and-column-layouts-with-flexbox-1k01)

### html

```
<div class='some-page-wrapper'>
  <div class='row'>
    <div class='column'>
      <div class='blue-column'>
        Some Text in Column One
      </div>
    </div>
    <div class='column'>
      <div class='green-column'>
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
  flex: 1;
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
  flex: 2;
}
```

##### Responsive:
```
@media screen and (min-width: 800px) {
  .column {
    flex: 1
  }

  .double-column {
    flex: 2
  }
}
```

References: [CSS Tricks' guide to flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
