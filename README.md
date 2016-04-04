# RWD
Generate responsive CSS classes using a single SCSS mixin and a variable map

[Edit on CodePen](http://codepen.io/craigmdennis/pen/Qydewy)

## Installation
Downaload and `@import` into your main `scss` file

### Create breakpoints
The current syntax is set up to use Bourbon Neat's `media` Breakpoint's `breakpoint` mixin.
```scss
$breakpoints: (
  mobile: max-width 47.9375em,
  tablet: 48em,
  hd: 62em
);
```

### Call the mixin
This will output content with the base class name as well as any breakpoints specified.
```scss
.component {
  @include rwd( mobile tablet hd ) {
    color: white;
    background: black;
  }
}

// .component {}
// .component--MQmobile {}
// .component--MQtablet {}
// .component--MQhd {}
```
If you only want a specific breakpoint and *no* base class, pass `false` as the second argument
```scss
.component {
  @include rwd( mobile, false ) {
    color: white;
    background: black;
  }
}

// .component--MQmobile {}
```

### Global settings
If you want to change the prefix you can add a settings map to your variables file

```scss
$rwdcss: (
  prefix: \@
);

// Default is "---MQ"
```

NOTE: Don't include the backslash in the HTML; it is purely to escape that character in CSS / SCSS
```scss
.component {
  @include rwd( mobile, true ) {
    color: white;
    background: black;
  }
}

// .component\@mobile {}
// <div class="component@mobile">This is only black <b>upto 48em</b></div>
```


### Use the classes
```html
<div class="component">This is always black</div>
<div class="component---MQmobile">This is only black <b>upto 48em</b></div>
<div class="component---MQtablet">This is only black at <b>48em wide</b></div>
<div class="component---MQhd">This is only black at <b>62em wide</b></div>
```
