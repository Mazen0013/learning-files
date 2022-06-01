# Transitioning Property Changes in CSS:

When interacting with a website, you might notice that many elements have `state`. For example, dropdowns can be in opened or closed states. Buttons might change color when focused or hovered. Modals appear and disappear.

By default, CSS switches the style of these states instantly.

- Using CSS transitions, we can interpolate between the initial state and the target state of the element.
- The transition between the two enhances the user experience by providing visual direction, support, and hints about the cause and effect of the interaction.

- To use transitions in CSS, you can use the various transition properties or the `transition` shorthand property.

---

## A) Transition Properties:

### 1- `transition-property` :

- The `transition-property` accepts one or more CSS property names in a comma-separated list.

### CSS Syntax

```
transition-property: none|all|property|initial|inherit;
```

### values:

`none` No property will get a transition effect

`all` Default value. All properties will get a transition effect

`(property)` Defines a comma separated list of CSS actual property names the transition effect is for

`initial` Sets this property to its default value. Read about initial

`inherit` Inherits this property from its parent element.

### examples:

```
div {
  transition-property: width, height;
}

div:hover {
  width: 300px;
  height: 300px;
}
```

### 2- `transition-duration` :

The `transition-duration` property is used to define the length of time that a transition will take to complete.

- it accepts time units, either in seconds (s) or milliseconds (ms) and defaults to 0s.

### CSS Syntax:

```
transition-duration: time|initial|inherit;
```

### values:

`time` Specifies how many seconds or milliseconds a transition effect takes to complete. Default value is 0s, meaning there will be no effect

`initial` Sets this property to its default value. Read about initial

`inherit` Inherits this property from its parent element

### examples:

```
div {
  transition-duration: 5s;
}
```

---

### 3) `transition-timing-function` :

we use the `transition-timing-function` property to vary the speed of a CSS transition over the course of the `transition-duration`.

### CSS Syntax:

```
transition-timing-function: linear|ease|ease-in|ease-out|ease-in-out|step-start|step-end|steps(int,start|end)|cubic-bezier(n,n,n,n)|initial|inherit;
```

### values:

`ease` Default value. Specifies a transition effect with a slow start, then fast, then end slowly (equivalent to cubic-bezier(0.25,0.1,0.25,1))
linear Specifies a transition effect with the same speed from start to end (equivalent to cubic-bezier(0,0,1,1))

`ease-in` Specifies a transition effect with a slow start (equivalent to cubic-bezier(0.42,0,1,1))

`ease-out` Specifies a transition effect with a slow end (equivalent to cubic-bezier(0,0,0.58,1))

`ease-in-out` Specifies a transition effect with a slow start and end (equivalent to cubic-bezier(0.42,0,0.58,1))

`step-start` Equivalent to steps(1, start)

`step-end` Equivalent to steps(1, end)

`steps(int,start|end)` Specifies a stepping function, with two parameters. The first parameter specifies the number of intervals in the function. It must be a positive integer (greater than 0). The second parameter, which is optional, is either the value "start" or "end", and specifies the point at which the change of values occur within the interval. If the second parameter is omitted, it is given the value "end"

`cubic-bezier(n,n,n,n)` Define your own values in the cubic-bezier function. Possible values are numeric values from 0 to 1

`initial` Sets this property to its default value.

`inherit` Inherits this property from its parent element.

### examples:

```
#div1 {transition-timing-function: linear;}
#div2 {transition-timing-function: ease;}
#div3 {transition-timing-function: ease-in;}
#div4 {transition-timing-function: ease-out;}
#div5 {transition-timing-function: ease-in-out;}

```

---

### 4) `transition-delay` :

Use the `transition-delay` property to specify the time at which a transition will start.

- If `transition-duration` is not specified, transitions will start instantly because the default value is 0s
- This property accepts a time unit, for example seconds (s) or milliseconds (ms).

### CSS Syntax:

```
transition-delay: (time)|initial|inherit;
```

### values:

`(time)` Specifies the number of seconds or milliseconds to wait before the transition effect will start

`initial` Sets this property to its default value.

`inherit` Inherits this property from its parent element.

### example :

```
div {
  transition-delay: 2s;
}
```

---

### 5) `transition` shorthand property:

the `transition` property is a shorthand property for:
`transition-property`

`transition-duration`

`transition-timing-function`

`transition-delay`

- it takes up to 4 values for the 4 properties separated by space.

### syntax:

```
transition: property duration timing-function delay|initial|inherit;
```

### values:

`transition-property` Specifies the name of the CSS property the transition effect is for

`transition-duration` Specifies how many seconds or milliseconds the transition effect takes to complete

`transition-timing-function` Specifies the speed curve of the transition effect

`transition-delay` Defines when the transition effect will start

`initial` Sets this property to its default value

`inherit` Inherits this property from its parent element

### examples:

```
.longhand {
  transition-property: transform;
  transition-duration: 300ms;
  transition-timing-function: ease-in-out;
  transition-delay: 0s;
}

.shorthand {
  transition: transform 300ms ease-in-out 0s;
}
```

---

### what can and can't `transition`?:

It is only possible to add animation ttransitions to elements that have a "_middle state_" between their start and their final states.

- For example, it's impossible to add transitions for `font-family`, because it's unclear what the "middle state" between `serif` and `monospace` should look like. On the other hand, it is possible to add transitions for `font-size` because its unit is a length that can be interpolated between.

![pic](transition/images/middlestate.webp)

---

## common transition properties:

### 1- `transform` :

The `transform` property applies a 2D or 3D transformation to an element.

- This property allows you to `rotate`, `scale`, `move`, `translate` or `skew` an element.

### syntax:

```
transform: none|(transform-functions)|initial|inherit;
```

### values:

`none` Defines that there should be no transformation

(transformation properties)

`matrix(n,n,n,n,n,n)` Defines a 2D transformation, using a matrix of six values

`matrix3d (n,n,n,n,n,n,n,n,n,n,n,n,n,n,n,n)` Defines a 3D transformation, using a 4x4 matrix of 16 values

`translate(x,y)` Defines a 2D translation

`translate3d(x,y,z)` Defines a 3D translation

`translateX(x)` Defines a translation, using only the value for the X-axis

`translateY(y)` Defines a translation, using only the value for the Y-axis

`translateZ(z)` Defines a 3D translation, using only the value for the Z-axis

`scale(x,y)` Defines a 2D scale transformation

`scale3d(x,y,z)` Defines a 3D scale transformation

`scaleX(x)` Defines a scale transformation by giving a value for the X-axis

`scaleY(y)` Defines a scale transformation by giving a value for the Y-axis

`scaleZ(z)` Defines a 3D scale transformation by giving a value for the Z-axis

`rotate(angle)` Defines a 2D rotation, the angle is specified in the parameter

`rotate3d(x,y,z,angle)` Defines a 3D rotation

`rotateX(angle)` Defines a 3D rotation along the X-axis

`rotateY(angle)` Defines a 3D rotation along the Y-axis

`rotateZ(angle)` Defines a 3D rotation along the Z-axis

`skew(x-angle,y-angle)` Defines a 2D skew transformation along the X- and the Y-axis

`skewX(angle)` Defines a 2D skew transformation along the X-axis

`skewY(angle)` Defines a 2D skew transformation along the Y-axis

`perspective(n)` Defines a perspective view for a 3D transformed element

`initial` Sets this property to its default value

`inherit` Inherits this property from its parent element.

![pic](transition/images/translate-rotate-scale-skew-demo.webp)

### examples:

```
div.a {
  transform: rotate(20deg);
}

div.b {
  transform: skewY(20deg);
}

div.c {
  transform: scaleY(1.5);
}
```

---

## transition triggers:

Your CSS must include a change of state and an event that triggers that state change for CSS transitions to activate.

- A typical example of such a trigger is the `:hover` pseudo-class. This pseudo-class matches when the user hovers over an element with their cursor.

Here is a list of some pseudo-classes and events that can trigger state changes in your elements:

- `:hover` : matches if the cursor is over the element.

`:focus` : matches if the element is focused.

`:focus-within` : matches if the element or any of its descendants are focused.

`:target` : matches when the current URL's fragment matches the element's id.

`:active` : matches when the element is being activated (typically when the mouse is pressed over it).
