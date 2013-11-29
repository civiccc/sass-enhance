# sass-enhance

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
curl -O https://raw.github.com/causes/sass-enhance/master/_sass-enhance.css.scss
```

#### `wget`

```bash
wget https://raw.github.com/causes/sass-enhance/master/_sass-enhance.css.scss
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
