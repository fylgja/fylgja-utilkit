# Utilkit (classes)

The default bundle of utilkit classes.

Each default is found here below, at section classes.
And can be enable separately if needed.

<details open><summary>Table of Contents</summary>

- [Text](#text)
- [Display](#display)
- [Flex](#flex)
- [Float](#float)
- [Width](#width)
- [Margin](#margin)
- [Padding](#padding)
- [Object](#object)
- [Table](#table)
- [Responsive classes](#responsive-classes)

</details>

By default the utilkit will load the default util classes.

Setting this value to `false` will disable any default classes.

Or if you only need parts pass them as an list to the `$enable-utilkit` var.

```scss
// Example: just text and media
$enable-utilkit: ("text", "media");
```

> [For overriding defaults, checkout the class builder doc](../class-builder/README.md#overriding-default-classes).

## Text

| Class (supports responsive) | Value              |
| --------------------------- | ------------------ |
| text-right                  | text-align: right  |
| text-left                   | text-align: left   |
| text-center                 | text-align: center |

| Class           | Value                  |
| --------------- | ---------------------- |
| text-uppercase  | text-align: uppercase  |
| text-lowercase  | text-align: lowercase  |
| text-capitalize | text-align: capitalize |

| Class       | Value               |
| ----------- | ------------------- |
| text-nowrap | white-space: nowrap |

## Display

| Class (supports responsive) | Value                 |
| --------------------------- | --------------------- |
| d-none                      | display: none         |
| d-block                     | display: block        |
| d-inline-block              | display: inline-block |
| d-flex                      | display: flex         |
| d-inline-flex               | display: inline-flex  |

## Flex

| Class (supports responsive) | Value                  |
| --------------------------- | ---------------------- |
| flex-row                    | flex-direction: row    |
| flex-colmun                 | flex-direction: column |

| Class (supports responsive) | Value                          |
| --------------------------- | ------------------------------ |
| justify-start               | justify-content: flex-start    |
| justify-center              | justify-content: center        |
| justify-end                 | justify-content: flex-end      |
| justify-between             | justify-content: space-between |
| justify-around              | justify-content: space-around  |

| Class (supports responsive) | Value                   |
| --------------------------- | ----------------------- |
| items-start                 | align-items: flex-start |
| items-center                | align-items: center     |
| items-end                   | align-items: flex-end   |
| items-baseline              | align-items: baseline   |
| items-stretch               | align-items: stretch    |

| Class (supports responsive) | Value                  |
| --------------------------- | ---------------------- |
| self-start                  | align-self: flex-start |
| self-center                 | align-self: center     |
| self-end                    | align-self: flex-end   |
| self-baseline               | align-self: baseline   |
| self-stretch                | align-self: stretch    |

| Class (supports responsive) | Value        |
| --------------------------- | ------------ |
| flex-grow-0                 | flex-grow: 0 |
| flex-grow-1                 | flex-grow: 1 |

| Class (supports responsive) | Value          |
| --------------------------- | -------------- |
| flex-shrink-0               | flex-shrink: 0 |
| flex-shrink-1               | flex-shrink: 1 |

| Class (supports responsive) | Value                   |
| --------------------------- | ----------------------- |
| flex-nowrap                 | flex-wrap: nowrap       |
| flex-wrap                   | flex-wrap: wrap         |
| flex-wrap-reverse           | flex-wrap: wrap-reverse |

## Float

| Class (supports responsive) | Value        |
| --------------------------- | ------------ |
| float-right                 | float: right |
| float-left                  | float: left  |

## Width

| Class (supports responsive) | Value          |
| --------------------------- | -------------- |
| w-auto                      | width: auto    |
| w-0                         | width: 0       |
| w-25                        | width: 25%     |
| w-33                        | width: 33.333% |
| w-50                        | width: 50%     |
| w-66                        | width: 66.667% |
| w-75                        | width: 75%     |
| w-100                       | width: 100%    |

## Margin

| Class  | Value         |
| ------ | ------------- |
| m-auto | margin: auto  |
| m-0    | margin: 0     |
| m-1    | margin: .5em  |
| m-2    | margin: 1em   |
| m-3    | margin: 1.5em |
| m-4    | margin: 2em   |

Each version also has an longhand version.

| Class      | Property                   |
| ---------- | -------------------------- |
| mt-{value} | margin-top                 |
| mr-{value} | margin-right               |
| mb-{value} | margin-bottom              |
| ml-{value} | margin-left                |
| mx-{value} | margin-right & margin-left |
| my-{value} | margin-top & margin-bottom |

## Padding

| Class | Value          |
| ----- | -------------- |
| p-0   | padding: 0     |
| p-1   | padding: .5em  |
| p-2   | padding: 1em   |
| p-3   | padding: 1.5em |
| p-4   | padding: 2em   |

Each version also has an longhand version.

| Class      | Property                     |
| ---------- | ---------------------------- |
| pt-{value} | padding-top                  |
| pr-{value} | padding-right                |
| pb-{value} | padding-bottom               |
| pl-{value} | padding-left                 |
| px-{value} | padding-right & padding-left |
| py-{value} | padding-top & padding-bottom |

## Object

| Class          | Value               |
| -------------- | ------------------- |
| object-cover   | object-fit: cover   |
| object-contain | object-fit: contain |

## Table

| Class       | Value               |
| ----------- | ------------------- |
| table-auto  | table-layout: auto  |
| table-fixed | table-layout: fixed |

## Responsive classes

Each breakpoint is a prefix added to the class.
Which is the `$breakpoints` key.

Example: `.md-{CLASS}`.

Defaults are:

```scss
$breakpoints: (
    xs: 0,
    sm: 480px,
    md: 768px,
    lg: 992px,
    xl: 1200px
) !default;
```
