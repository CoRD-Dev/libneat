[![Bourbon Neat](http://neat.bourbon.io/images/logotype.svg)](http://neat.bourbon.io/)

**Neat** is an open source fluid grid framework built on top of [Bourbon](http://bourbon.io) with the aim of being easy enough to use out of the box and flexible enough to customize down the road.


Requirements
===
- Sass 3.2+
- Bourbon 2.1+

Install Instructions
===
Install [Bourbon](https://github.com/CoRD-Dev/libbourbon#install-instructions) and [Bitters](https://github.com/CoRD-Dev/libbitters#install-instructions) (optional).

`cd` to your projects local repository and run:

```bash
git submodule add https://github.com/CoRD-Dev/libneat.git sass/neat
```
(`sass/neat` should be the directory your sass/scss files are kept +/neat.)

The generated folder will contain all Neats files.

Import Neat after Bourbon in your `application.css.scss`. All additional stylesheets should be imported below Neat:

```scss
@import "bourbon/bourbon";
@import "neat/neat";

// All other imports
```


Getting started
===

First off, if you are planning to override the default grid settings (12 columns), it is recommended to create a `_grid-settings.scss` file for that purpose. Make sure to import it right *before* importing Neat:

```scss
@import "bourbon/bourbon";
@import "grid-settings";
@import "neat/neat";
```

In your newly created  `_grid-settings.scss`, import `neat-helpers` if you are planning to use `new-breakpoint()`, then define your new variables:

```scss
@import "neat/neat-helpers";

// Change the grid settings
$column: 90px;
$gutter: 30px;
$grid-columns: 10;
$max-width: em(1088);

// Define your breakpoints
$tablet: new-breakpoint(max-width 768px 8);
$mobile: new-breakpoint(max-width 480px 4);
```

See the [docs](http://neat.bourbon.io/docs/#variables) for a full list of settings.

Next, include the `outer-container` mixin in the topmost container (to which the `max-width` setting will be applied):

```scss
div.container {
  @include outer-container;
}
```

Then use `span-columns` on any element to specify the number of columns it should span:

```scss
div.element {
  @include span-columns(6);
}
```

If the element's parent isn't the top-most container, you need to add the number of columns of the parent element to keep the right proportions:

```scss
div.container {
  @include outer-container;
  div.parent-element {
    @include span-columns(8);
    div.element {
      @include span-columns(6 of 8);
    }
  }
}
```

To make your layout responsive, use the `media()` mixin to modify both the grid and the layout:

```scss
.my-class {
  @include media($mobile) { // As defined in _grid-settings.scss
    @include span-columns(2);
  }
}

// Compiled CSS
@media screen and (max-width: 480px) {
  .my-class {
    display: block;
    float: left;
    margin-right: 7.42297%;
    width: 46.28851%; // 2 columns of the total 4 in this media context
  }
  .my-class:last-child {
    margin-right: 0;
  }
}
```

By setting `$visual-grid` to `true`, you can display the base grid in the background (default) or as an overlay. You can even change the color and opacity of the grid-lines by overriding the default settings as detailed in the section below. Keep in mind that on Webkit, rounding errors in the fluid grid might result in the overlay being few pixels off.

The visual grid reflects the changes applied to the grid via the `new-breakpoint()` mixin, as long as the media contexts are defined *before* importing Neat.

Browser support
===
- Firefox 3.5+
- Safari 4.0+
- Chrome 4.0+
- Opera 9.5+
- IE 9+ (Visual grid is IE10 only)
- IE 8 with [selectivizr](http://selectivizr.com) (no `media()` support)

Links
=====

- Read the [online documentation](http://neat.bourbon.io/docs/).
- Add the docset to [Dash](http://kapeli.com/dash) 1.8+ (Preferences **>** Downloads **>** + *Add Docset Feed* **>** `http://neat.bourbon.io/docset/Neat.xml`)
- Ask questions on [Stack Overflow](http://stackoverflow.com/questions/tagged/neat+bourbon). Don't forget to tag them`bourbon` and `neat`.
- Suggest features or file bugs in [Issues](https://github.com/thoughtbot/neat/issues).
- Read the [contribution guidelines](https://github.com/thoughtbot/neat/blob/master/CONTRIBUTING.md).
- Say hi to [@kaishin](https://twitter.com/kaishin) and [@kylefiedler](https://twitter.com/kylefiedler).


Credits & License
=================

![thoughtbot](http://thoughtbot.com/images/tm/logo.png)

Bourbon is maintained and funded by [thoughtbot, inc](http://thoughtbot.com/). Follow [@thoughtbot](http://twitter.com/thoughtbot) on Twitter.

Bourbon Neat is Copyright © 2012-2013 thoughtbot. It is free software, and may be redistributed under the terms specified in the LICENSE file.
