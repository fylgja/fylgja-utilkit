# Utilkit (functions)

<details><summary>Table of Contents</summary>

- [str-replace](#str-replace)
- [strip-unit](#strip-unit)
- [luminance](#luminance)
- [contrast-ratio](#contrast-ratio)
- [contrast](#contrast)
- [map-deep-get](#map-deep-get)
- [encode-svg](#encode-svg)
- [if-mq](#if-mq)
- [loop-mq](#loop-mq)

</details>

## str-replace

Replace value in string

```scss
@debug str-replace(
    "Lorem ipsum dolor sit amet.",
    "ipsum",
    "😎"
);
// output = Lorem 😎 dolor sit amet.
```

## strip-unit

Strips the unit from a number.

```scss
@debug strip-unit(1337px);
// output = 1337
```

## luminance

Return the luminance value of the color.

```scss
@debug luminance(#03a9f4);
// output = 0.3492694673
```

## contrast-ratio

Return the contrast ratio value of the color.

_Used as helper for the contrast function._

```scss
@debug contrast-ratio(#03a9f4, #222);
// output = 7.9853893463
```

## contrast

Checks the contrast against the color
and returns the dark color or light color.

```scss
@debug contrast(#03a9f4, #222, #fff);
// output = #222
```

The 2de and 3de value are optional.
Just using `contrast(#03a9f4)` will result in the same output.
But the dark and light color will be used from the default settings.
Which you can change via;

```scss
$config-contrast: (
    min: 4.5,
    dark: #222,
    light: #fff
);
```

## map-deep-get

Return value from nested map.

```scss
$food-colors: (
    "fruits": (
        "apple": "green",
        "banana": "yellow"
    )
);

@debug map-get-deep($food-colors, "fruits", "apple");
// output = green
```

## encode-svg

Load svg as dataUri.

Usefull if you don't want an dependency to an external svg image source.

```scss
@debug encode-svg('<svg viewBox="0 0 24 24"><path d="M0 0h24v24H0z" fill="none"/><path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/></svg>');
// output = url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath d='M0 0h24v24H0z' fill='none'/%3E%3Cpath d='M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z'/%3E%3C/svg%3E")
```

_Based on [jacob-e's codepen](https://codepen.io/jakob-e/pen/doMoML)_

## if-mq

Check if media query is needed or not.

Usefull for sass functions and mixins.

```scss
@each $mq, $var in $map {
    @include if-mq($mq, $feature: "min-width") {
        .if-mq {
            width: $var;
        }
    }
}
```

_`$feature` is not required, default = min-width_

## loop-mq

Loop through `$breakpoints` map to generate css classes based on the content passed.

```scss
@include loop-mq {
    &-float-start {
        float: start;
    }
}
```

Output: 

```css
.float-start {
    float: start;
}

@media (min-width: 480px) {
    .sm-float-start {
        float: start;
    }
}
```

`loop-mq` accepts the following params:

* `$class` pass class directly to mixin
  * default is empty,
    and normally classes can be nested inside,
    but it is usefull with `$use-xs-name` set to false
* `$use-xs-name`: if the xs value is also added as class name
  * default is true
* `$part-of`: make mq of loop part of parent class
  * default is false
* `$map`: map to loop trough
  * default is `$breakpoints`.
