# sass-enhance

[![Bower version](https://badge.fury.io/bo/sass-enhance.svg)](http://badge.fury.io/bo/sass-enhance)

Sass mixins that enable the implementaiton of a responsive design with a
progressive enhancement approach. Originally written for use at
[Causes](https://github.com/causes).

## Installing

### Bower

To install sass-enhance using [Bower](http://bower.io), simply run:

```bash
bower install sass-enhance
```

If you'd like to save sass-enhance as a dependency in your project's
`bower.json` manifest file, run:

```bash
bower install --save sass-enhance
```

### Manually

Simply download the `_sass-enhance.css.scss` file from this repo and place it
somewhere useful.

#### `curl`

```bash
curl -O https://raw.githubusercontent.com/causes/sass-enhance/master/_sass-enhance.css.scss
```

#### `wget`

```bash
wget https://raw.githubusercontent.com/causes/sass-enhance/master/_sass-enhance.css.scss
```

## Using

sass-enhance defines mixins for media queries, `enhance` and `degrade`.

These mixins each take a breakpoint as an argument, and a block of styles to
apply when that breakpoint is activated. Optionally, you can specify ranged
breakpoints using `until`.

Breakpoints can be named, as defined in the `$breakpoint-max-widths` variable
(e.g. "tablet"), or arbitrary widths (e.g. "720px").

### `enhance`

The `enhance` mixin is used to apply styles to a selector as the viewport gets
wider. It can be used to progressively enhance a page. We prefer using
`enhance` over `degrade` because it is a mobile-first implementation that tends
to be simpler in its execution.

To adjust the padding from 1em to 2em at the desktop breakpoint and wider, you
could use the following SCSS:

```scss
.my-selector {
  padding: 1em;

  @include enhance(desktop) {
    padding: 2em;
  }
}
```

If you wanted to only apply a different amount of padding for only the tablet
viewport width and nothing wider or narrower, you could use the following SCSS:

```scss
.my-selector {
  padding: 1em;

  @include enhance(tablet until desktop) {
    padding: 2em;
  }
}
```


### `degrade`

There are some cases where `enhance` does not work or make sense. In these
cases, it is okay to use `degrade` to gracefully degrade the styles as the
viewport gets narrower.

To adjust the padding from 2em to 1em at the tablet breakpoint and narrower,
you could use the following SCSS:

```scss
.my-selector {
  padding: 2em;

  @include degrade(tablet) {
    padding: 1em;
  }
}
```

Note: this produces functionally equivalent styles as the first example.

Likewise, if you wanted to only apply a different amount of padding for only
the tablet viewport width and nothing wider or narrower, you could use the
following SCSS:

```scss
.my-selector {
  padding: 2em;

  @include degrade(tablet until small-tablet) {
    padding: 1em;
  }
}
```

### `breakpoint-min-width`

This mixin will return the min-width of a named breakpoint. The min-width is
defined as the pixel value of the previous named breakpoint, plus one pixel.

```scss
.my-selector {
  min-width: breakpoint-min-width(tablet); // 641px with default settings
}
```

### `breakpoint-max-width`

Returns the max-width of a named breakpoint. This is the raw pixel value
associated with the named breakpoint in the `$breakpoint-max-widths` variable.

```scss
.my-selector {
  max-width: breakpoint-max-width(tablet); // 959px with default settings
}
```

## Configuring breakpoints

To configure your breakpoints, set the `$breakpoint-max-widths` variable
*before importing sass-enhance*.

This variable is a comma separated list of breakpoint names and max-width
pairs. You can choose whatever names and widths you prefer. The default is
something like:

```scss
$breakpoint-max-widths: mobile           360px,
                        mobile-landscape 500px,
                        small-tablet     640px,
                        tablet           959px,
                        desktop          99999px;
```

## License

Released under the MIT License.
