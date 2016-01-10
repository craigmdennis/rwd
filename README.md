# RWD
Generate responsive CSS classes using a single SCSS mixin and a variable map

[Edit on CodePen](http://codepen.io/craigmdennis/pen/Qydewy)

## Installation
Downaload and `@import` into your main `scss` file

### Create breakpoints
The current syntax is set up to use Bourbon Neat's `@media` mixin
```scss
$breakpoints: (
  mobile: max-width 47.9375em,
  tablet: 48em,
  hd: 62em
);
```

### Call the mixin
```scss
.component {
  @include rwd( mobile tablet hd ) {
    color: white;
    background: black;
  }
}
```

### Use the classes
```html
<div class="component">This is always black</div>
<div class="component---MQmobile">This is only black <b>upto 48em</b></div>
<div class="component---MQtablet">This is only black at <b>48em wide</b></div>
<div class="component---MQhd">This is only black at <b>62em wide</b></div>
```
