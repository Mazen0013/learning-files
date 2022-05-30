# The CSS Grid layout:

The CSS Grid Layout Module offers a grid-based layout system, with `rows` and `columns`, making it easier to design web pages without having to use floats and positioning.

![pic](/images/grid.png)

# Grid Terminology:

### 1- Grid `container`:

The element on which display: grid is applied. It’s the direct parent of all the grid items.

```
<div class="container">
  <div class="item item-1"> </div>
  <div class="item item-2"> </div>
  <div class="item item-3"> </div>
</div>
```

### 2- Grid `Item`:

The children (i.e. direct descendants) of the grid container.

```
<div class="container">
  <div class="item"> </div>
  <div class="item">
    <p class="sub-item"> </p>
  </div>
  <div class="item"> </div>
</div>
```

### 3- Grid `Lines`:

The dividing lines that make up the structure of the grid. They can be either vertical (_“column grid lines”_) or horizontal (_“row grid lines”_).
![pic](/images/terms-grid-line.svg)

### 4- Grid `Cell`:

The space between two adjacent row and two adjacent column grid lines.

![pic](/images/terms-grid-cell.svg)

### 5- Grid `Track`:

the columns or rows of the grid.

![pic](/images/terms-grid-track.svg)

### Grid `Area`:

The total space surrounded by four grid lines. A grid area may be composed of any number of grid cells.

![pic](/images/terms-grid-area.svg)

# Grid Properties:

### A) Properties for the Parent (Grid Container) :

1- `display` :

An HTML element becomes a grid container when its display property is set to `grid` or `inline-grid`.

```
.container {
  display: grid | inline-grid;
}
```

---

2- `grid-template-columns` / `grid-template-rows` :

- specifies the size of the columns/ rows and how many columns/ rows in a grid layout.
- it includes a space-separated list of values.

`grid-template-columns`:

### CSS syntax:

```
grid-template-columns: none|auto|max-content|min-content|(length)|initial|inherit;
```

### property values:

`none`: Default value. Columns are created if needed.

`auto`: The size of the columns is determined by the size of the container and by the size of the content of the items in the column.

`max-content`: Sets the size of each column to depend on the largest item in the column.

`min-content`: Sets the size of each column to depend on the smallest item in the column.

(_`length`_): Sets the size of the columns, by using a legal length value. (e.g. px, rem, percentage, fr).

`initial`: Sets this property to its default value.

`inherit`: Inherits this property from its parent element.

e.g.

```
.grid-container {
  display: grid;
  grid-template-columns: 30px 200px auto 100px;
}
```

If your definition contains repeating parts, you can use the repeat() notation to streamline things:

```
.container {
  grid-template-columns: repeat(3, 20px);
}
```

The `fr` unit allows you to set the size of a track as a fraction of the free space of the grid container. For example, this will set each item to one third the width of the grid container:

```
.container {
  grid-template-columns: 1fr 1fr 1fr;
}
```

The free space is calculated after any non-flexible items. In this example the total amount of free space available to the fr units doesn’t include the 50px:

```
.container {
  grid-template-columns: 1fr 50px 1fr 1fr;
}
```

`grid-template-rows`:

### CSS syntax:

```
grid-template-rows: none|auto|max-content|min-content|(length)|initial|inherit;
```

(the property values are the same as the ones above)

e.g.

```
.grid-container {
  display: grid;
  grid-template-rows: 100px 300px;
}
```

---

3- `grid-template-areas` :

Defines a grid template by referencing the names of the grid areas which are specified with the grid-area property. Repeating the name of a grid area causes the content to span those cells. A period signifies an empty cell. The syntax itself provides a visualization of the structure of the grid.

### CSS Syntax:

```
grid-template-areas: none|(itemnames);
```

`none`: Default value. No named grid areas.

_`itemnames`_: A sequence of actual names that specifies how each columns and row should display.

```
.container {
  grid-template-areas:
    "<grid-area-name> | . | none | ..."
    "...";
}
```

`<grid-area-name>` : here you write the actual name of a grid area specified with `grid-area` property.

`.` – a period signifies an empty grid cell.

example:

```
.item-a {
  grid-area: header;
}
.item-b {
  grid-area: main;
}
.item-c {
  grid-area: sidebar;
}
.item-d {
  grid-area: footer;
}

.container {
  display: grid;
  grid-template-columns: 50px 50px 50px 50px;
  grid-template-rows: auto;
  grid-template-areas:
    "header header header header"
    "main main . sidebar"
    "footer footer footer footer";
}
```

That’ll create a grid that’s four columns wide by three rows tall. The entire top row will be composed of the header area. The middle row will be composed of two main areas, one empty cell, and one sidebar area. The last row is all footer.

![pic](/images/template-areas.svg)

---

4- `grid-template`:

A shorthand for setting `grid-template-rows`, `grid-template-columns`, and `grid-template-areas` in a single declaration.

CSS syntax:

```
.container {
  grid-template: none | <grid-template-rows> / <grid-template-columns>;
}
```

`none` – sets all three properties to their initial values

`<grid-template-rows> / <grid-template-columns>` – sets grid-template-columns and grid-template-rows to the specified values, respectively, and sets grid-template-areas to none

- It also accepts a more complex but quite handy syntax for specifying all three. Here’s an example:

```
.container {
  grid-template:
     "header header header" 25px
     "footer footer footer" 25px
    / auto 50px auto;
}
```

that's equivalent to this:

```
.container {
  grid-template-rows: 25px 25px ;
  grid-template-columns: auto 50px auto;
  grid-template-areas:
    "header header header"
    "footer footer footer";
}
```

---

5-`grid-gap` :

- defines the size of the gap between the rows and columns in a grid layout,
- and is a shorthand property for the following properties:

`row-gap`,

`column-gap`

- it takes a length value (px, rem, ....)

example:

```
.container {
  grid-template-columns: 100px 50px 100px;
  grid-template-rows: 80px auto 80px;
  column-gap: 10px;
  row-gap: 15px;
}
```

or like this using the shorthand property:

```
.container {
  grid-template-columns: 100px 50px 100px;
  grid-template-rows: 80px auto 80px;
  gap: 15px 10px;
}
```

that would look like this:

![pic](/images/gap.svg)

The gutters are only created between the columns/rows, not on the outer edges.

---

6- `justify-items` :

- Aligns grid items along the inline (row) axis
- This value applies to all grid items inside the container.

### syntax:

```
.container {
  justify-items: start | end | center | stretch;
}
```

### values:

`start` – aligns items to be flush with the start edge of their cell

`end` – aligns items to be flush with the end edge of their cell

`center` – aligns items in the center of their cell.

`stretch` – fills the whole width of the cell (this is the default)

examples:

```
.container {
  justify-items: start;
}
```

![pic](/images/justify-items-start.svg)

```
.container {
  justify-items: stretch;
}
```

![pic](/images/justify-items-stretch.svg)

---

7- `align-items` :

- Aligns grid items along the block (column) axis.

- This value applies to all grid items inside the container.

### syntax:

```
.container {
  align-items: start | end | center | stretch;
}
```

### values:

`stretch` – fills the whole height of the cell (this is the default)

`start` – aligns items to be flush with the start edge of their cell

`end` – aligns items to be flush with the end edge of their cell

`center` – aligns items in the center of their cell

### examples:

```
.container {
  align-items: start;
}
```

![pic](/images/align-items-start.svg)

```
.container {
  align-items: center;
}
```

![pic](/images/align-items-center.svg)

```
.container {
  align-items: stretch;
}
```

![pic](/images/align-items-stretch.svg)

-This behavior can also be set on individual grid items via the `align-self` property.

---

8- `place-items` :

- place-items sets both the align-items and justify-items properties in a single declaration.
- it can take two values (the first one sets `align-items` and the second one sets `justify-items`)
- If the second value is omitted, the first value is assigned to both properties.

```
.container {
    display: grid;
    place-items: center;
}
```

---

9- `justify-content` :

- Sometimes the total size of your grid might be less than the size of its grid container.
  This could happen if all of your grid items are sized with non-flexible units like px. In this case you can set the `alignment` of the grid within the grid container.
- This property aligns the grid along the inline (row) axis.

### syntax:

```
.container {
  justify-content: start | end | center | stretch | space-around | space-between | space-evenly;
}
```

### values:

`start` – aligns the grid to be flush with the start edge of the grid container

`end` – aligns the grid to be flush with the end edge of the grid container

`center` – aligns the grid in the center of the grid container

`stretch` – resizes the grid items to allow the grid to fill the full width of the grid container

`space-around` – places an even amount of space between each grid item, with half-sized spaces on the far ends

`space-between` – places an even amount of space between each grid item, with no space at the far ends

`space-evenly` – places an even amount of space between each grid item, including the far ends

### Examples:

```
.container {
  justify-content: start;
}
```

![pic](/images/justify-content-start.svg)

```
.container {
  justify-content: space-around;
}
```

![pic](/images/justify-content-space-around.svg)

```
.container {
  justify-content: space-between;
}
```

![pic](/images/justify-content-space-between.svg)

```
.container {
  justify-content: space-evenly;
}
```

![pic](/images/justify-content-space-evenly.svg)

---

10- `align-content` :

in the same case that the total size of your grid is less than the size of its grid container, you can set the alignment of the grid within the grid container.

- This property aligns the grid along the block (column) axis.

### syntax:

```
.container {
 align-content: start | end | center | stretch | space-around | space-between | space-evenly;
}
```

### values:

`start` – aligns the grid to be flush with the start edge of the grid container

`end` – aligns the grid to be flush with the end edge of the grid container

`center` – aligns the grid in the center of the grid container

`stretch` – resizes the grid items to allow the grid to fill the full height of the grid container

`space-around` – places an even amount of space between each grid item, with half-sized spaces on the far ends

`space-between` – places an even amount of space between each grid item, with no space at the far ends

`space-evenly` – places an even amount of space between each grid item, including the far ends

### examples:

```
.container {
  align-content: start;
}
```

![pic](/images/align-content-start.svg)

```
.container {
  align-content: center;
}
```

![pic](/images/align-content-center.svg)

```
.container {
  align-content: space-around;
}
```

![pic](/images/align-content-space-around.svg)

---

11- `place-content` :

sets both the `align-content` and `justify-content` properties in a single declaration.

- it can take two values, The first value sets `align-content`, the second value `justify-content`
- If the second value is omitted, the first value is assigned to both properties.

---
