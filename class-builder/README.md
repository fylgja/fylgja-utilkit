# Utilkit (class builder)

But if you need more control on what util classes are loaded.

<details open><summary>Table of Contents</summary>

- [Change name](#change-name)
- [Set states (focus, hover)](#set-states-focus-hover)
- [Add responsive behavior](#add-responsive-behavior)
- [Make value important](#make-value-important)
- [Build longhand properties from just the shorthand](#build-longhand-properties-from-just-the-shorthand)
- [Overriding default classes](#overriding-default-classes)
- [Create classes from utils](#create-classes-from-utils)

</details>

You can make your own util classes via the `$config-utils` settings.
This is a simple as writing a css property class.

**Example:**

```scss
$config-utils: (
    "display": (block, none),
    "text-align": right
);
```

```css
.display-block {
    display: block;
}

.display-none {
    display: none;
}

.text-align-right {
    text-align: right;
}
```

If you need value that can not be a class name use a value key.

```scss
$config-utils: (
    "width": ("50": 50%)
);
```

The `$config-utils` settings map can do more
than just the simple examples mentioned before.

For this you need to pass any values in the key `"values"`

For any of the options you must use the key `"options"`
and one of the possible options, below.

## Change name

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
);
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

## Set states (focus, hover)

Need focus or hover states.
Simple pass them as an option like this:

```scss
$config-utils: (
    "color": (
        "values": ("badass-blue": #1976d2),
        "options": ("hover")
    )
);
```

```css
.color-badass-blue,
.hover-color-badass-blue:hover {
    color: #1976d2;
}
```

This will create both the default and hover state.

## Add responsive behavior

Need responsive behavior for your util class.
Simple pass the options `"responsive"`.

```scss
$config-utils: (
    "text-align": (
        "values": (right, left),
        "options": ("responsive")
    )
);
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

## Make value important

Have an util that needs to override any style.
Simple pass the options `"important"`.

```scss
$config-utils: (
    "display": (
        "values": (none),
        "options": ("important")
    )
);
```

```css
.display-none {
    display: none !important;
}
```

## Build longhand properties from just the shorthand

Altrough can make each css property your self.
Sometimes it is usefull to output multiple version of the shorthand property.

Just as with the options this requires the values in the key values.
And each longhand property in `"properties"`.

```scss
$config-utils: (
    "padding": (
        "values": ("1": .5rem),
        "properties": ("right", "left", "x")
    )
);
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

## Overriding default classes

If you enabled the default util classes.
and also want to add your own via the builder.

Then there are some things you need take note of.

Since the builder uses nested maps.
Your new value will not be added.
If there is already an property that you want to add to.

To change this unset the default part in the `$enable-utilkit` var.
Or change the config related to that default, e.g. `$config-utilkit-display`.

## Create classes from utils

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
