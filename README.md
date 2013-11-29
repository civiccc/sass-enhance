# sass-enhance

Sass mixins that enable the implementaiton of a responsive design with a
progressive enhancement approach. Originally written for use at
[Causes](https://github.com/causes).

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
