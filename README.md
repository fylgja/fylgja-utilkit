# Fylgja UtilKit 🛠

[![NPM version](https://img.shields.io/npm/v/@fylgja/utilkit.svg)](https://www.npmjs.org/package/@fylgja/utilkit)

The UtilKit is an helper package.
And contains sass functions and mixins.
Which makes some complex tasks easier.

And only has an focus on extending native sass functions.
So redundant functions like prefixeing CSS are a no go.

<details><summary>Table of Contents</summary>

- [Installation](#Installation)
- [How to use](#How-to-use)
  - [Utils Functions](#Utils-Functions)
    - [str-replace](#str-replace)
    - [strip-unit](#strip-unit)
    - [luminance](#luminance)
    - [contrast-ratio](#contrast-ratio)
    - [contrast](#contrast)
    - [map-deep-get](#map-deep-get)
    - [encode-svg](#encode-svg)
    - [if-mq](#if-mq)
    - [loop-mq](#loop-mq)
  - [Utils Classes](#Utils-Classes)

</details>

## Installation

```bash
npm install @fylgja/utilkit --save-dev
```

## How to use

Include the utilkit package in to your code via;

```scss
@import "@fylgja/utilkit/utilkit";
```

### Utils Functions

#### str-replace

Replace value in string

```scss
@debug str-replace(
    "Lorem ipsum dolor sit amet.",
    "ipsum",
    "😎"
);
// output = Lorem 😎 dolor sit amet.
```

#### strip-unit

Strips the unit from a number.

The opposite of the native function [`unit()`](https://sass-lang.com/documentation/functions/math#unit)

```scss
@debug strip-unit(1337px);
// output = 1337
```

#### luminance

Return the luminance value of the color.

```scss
@debug luminance(#03a9f4);
// output = 0.3492694673
```

#### contrast-ratio

Return the contrast ratio value of the color.

Used as helper for the contrast function.

```scss
@debug contrast-ratio(#03a9f4, #222);
// output = 7.9853893463
```

#### contrast

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

#### map-deep-get

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

#### encode-svg

Load svg as dataUri.

Usefull if you don't want an dependency to an external svg image source.

```scss
@debug encode-svg('<svg viewBox="0 0 24 24"><path d="M0 0h24v24H0z" fill="none"/><path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/></svg>');
// output = url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath d='M0 0h24v24H0z' fill='none'/%3E%3Cpath d='M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z'/%3E%3C/svg%3E")
```

_Based on [jacob-e's codepen](https://codepen.io/jakob-e/pen/doMoML)_

#### if-mq

Check if media query is needed or not.

Usefull for sass functions and mixins.

#### loop-mq

Loop through breakpoint map to generate css classes based on the default passed.

```scss
.float {
    @include loop-mq {
        &-left {
            float: left;
        }
    }
}
```

Output: 

```css
.float-left {
    float: left;
}

@media (min-width: 480px) {
    .float-sm-left {
        float: left;
    }
}

@media (min-width: 768px) {
    .float-md-left {
        float: left;
    }
}
```

`loop-mq` accepts 2 params:

* `$part-of`: if the class the mq class is part of the parent class
  * default is true
* `$map`: map the loop trough
  * default is $breakpoints.

### Utils Classes

By default the utilkit will not genarate 

