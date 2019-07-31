# Fylgja UtilKit

[![NPM version](https://img.shields.io/npm/v/@fylgja/utilkit.svg)](https://www.npmjs.org/package/@fylgja/utilkit)

The UtilKit is a small helper package. that can make complex tasks easier.

By offering scss functions, mixins and a utility-class builder.

And only has an focus on extending native sass functions.
So redundant functions like prefixeing CSS are a no go.

<details><summary>Table of Contents</summary>

- [Installation](#installation)
- [How to use](#how-to-use)
  - [Utils Functions](#utils-functions)
    - [str-replace](#str-replace)
    - [strip-unit](#strip-unit)
    - [luminance](#luminance)
    - [contrast-ratio](#contrast-ratio)
    - [contrast](#contrast)
    - [map-deep-get](#map-deep-get)
    - [encode-svg](#encode-svg)
    - [if-mq](#if-mq)
    - [loop-mq](#loop-mq)
  - [Utils Classes](#utils-classes)
    - [Config Utils](#config-utils)
    - [Options intro](#options-intro)
    - [Option change name](#option-change-name)
    - [Option states (focus, hover)](#option-states-focus-hover)
    - [Option responsive behavior](#option-responsive-behavior)
    - [Option important](#option-important)
    - [Build longhand properties from shorthand](#build-longhand-properties-from-shorthand)
    - [Extending](#extending)
- [FAQ](#faq)

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

_Used as helper for the contrast function._

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

### Utils Classes

By default the utilkit will not genarate any css utilities.

These can be made via the `$config-utils` settings.
_[More on that below.](#config-utils)_

Or via the default bundels which you can enable,
by setting the following variables to true.

* `enable-utils-base`: Loads all 3 below
* `enable-utils-flex`: Loads flex utils
* `enable-utils-spacing`: Loads:
  * margin with media queries
  * padding with media queries
* `enable-utils-content`: Loads:
  * text-align with media queries
  * float utils with media queries
  * object-fit

#### Config Utils

But if you need more control.
You can make your own util classes via the `$config-utils` settings.
This is a simple as writing a css property class.

**Example:**

```scss
$config-utils: (
    "display": (block, none),
    "text-align": right
)
```

```css
.display-block {
    display: block;
}

.display-block {
    display: block;
}

.text-align-right {
    display: block;
}
```

If you need value that can not be a class name use a value key.

```scss
$config-utils: (
    "width": (
        "50": 50%
    )
)
```

#### Options intro

The `$config-utils` settings map can do more
than just the simple examples mentioned before.

For this you need to pass any values in the key `"values"`

For any of the options you must use the key `"options"`
and one of the possible options:

* [value-name](#option-change-name)
* [property-name](#option-change-name)
* [property-short](#option-change-name)
* [hover](#option-states-focus-hover)
* [focus](#option-states-focus-hover)
* [responsive](#option-responsive-behavior)
* [important](#option-important)

#### Option change name

If you don't like the output name.
For example with text-align.

Than add the key `"options"` to the property key.
And add the option `"value-name"`.
This will only use the value key as name for the class.

```scss
$config-utils: (
    "text-align": (
        "values": (
            "text-right": right,
            "text-left": left,
        )
        "options": ("value-name")
    )
)
```

```css
.text-right {
    text-align: right;
}

.text-left {
    text-align: left;
}
```

You also reverse this behavior to use only the `"property-name"`.
But this is only usefull for single valued properties.

E.g. if you only need the wrap from `flex-wrap: wrap;`.
since writting flex-wrap-wrap feels super weird.

Or if you need to property name super short (one character).
Use `"property-short"`.

Some properties have automatic name changes, if no option is set.
We wanted to keep this list small since everyone has diffrent needs and wishes.

* background-color = bg
* text-align = text
* text-decoration = text
* object-fit = object
* object-position = object

_Values with the same name will not conflit._
_Since there css values are diffrent from the other property_

To override this default behavior
simpley use the `"value-name"` as mention above.

#### Option states (focus, hover)

Need focus or hover states.
Simple pass them as an option like this:

```scss
$config-utils: (
    "color": (
        "values": (
            "badass-blue": #1976d2
        ),
        "options": ("hover")
    )
)
```

```css
.color-badass-blue,
.hover-color-badass-blue:hover {
    color: #1976d2;
}
```

This will create both the default and hover state.

#### Option responsive behavior

Need responsive behavior for your util class.
Simple pass the options `"responsive"`.

```scss
$config-utils: (
    "text-align": (
        "values": (right, left),
        "options": ("responsive")
    )
)
```

```css
.text-align-right {
    text-align: right;
}

@media (min-width: 768px) {
    .md-text-align-right {
        text-align: right;
    }
}
```

This will create both the default util class
and all version from the media queries map `$config-util-breakpoints`.

_The default map values are the same as `$breakpoints`,_
_from the loop-mq function_

#### Option important

Have an util that needs to override any style.
Simple pass the options `"important"`.

```scss
$config-utils: (
    "display": (
        "values": (none),
        "options": ("important")
    )
)
```

```css
.display-none {
    display: none !important;
}
```

#### Build longhand properties from shorthand

Altrough can make each css property your self.
Sometimes it is usefull to output multiple version of the shorthand property.

Just as with the options this requires the values in the key values.
And each longhand property in `"properties"`.

```scss
$config-utils: (
    "padding": (
        "values": ("1": .5rem,),
        "properties": ("right", "left", "x")
    )
)
```

```css
.padding-1 {
  padding: .5rem;
}

.padding-right-1 {
  padding-right: .5rem;
}

.padding-left-1 {
  padding-left: .5rem;
}

.padding-x-1 {
  padding-right: .5rem;
  padding-left: .5rem;
}
```

> ⚠️ Altrough this makes creating utils super easy.
> It also creates allot of css.
> So use with caution!

#### Extending

Each `$config-utils` setting will also create an extend placeholder.

The extend placeholder has the same name as the util from the `$config-utils`.
With the prefix util.

This can be used to build classes similar to TailwindCSS's `@apply`.

```scss
.card {
    @extend %util-border-default;
    @extend %util-radius-1;
    @extend %util-bg-white;
    @extend %util-p-6;
}
```

## FAQ

<details><summary>Can I add more automatic names to the Util class</summary>

Yes!

Simple create an issue or PR with the why.

</details>

<details><summary>Why use Util class Extends</summary>

The extend option is and option and nothing more.

We don't support the use of `@extend`.
But for some cases this could make sense.

</details>

<details><summary>Why not TailwindCSS instead the Util class</summary>

Util class is an SCSS helper so.

If you already using SCSS this is easier to add to your project.
Also Util class does not load anything if you don't specifically set it.

</details>
