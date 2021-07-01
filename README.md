> :warning: This package has been deprecated
> 
> @fylgja/utilkit has been replaced and split in to 2 new packages,
> for the sass functions see [@fylgja/sass](https://github.com/fylgja/fylgja-sass)
> and for CSS utility classes see [@fylgja/utilpack](https://github.com/fylgja/fylgja/tree/main/components/utilpack)

# Fylgja UtilKit

[![NPM version](https://img.shields.io/npm/v/@fylgja/utilkit.svg)](https://www.npmjs.org/package/@fylgja/utilkit)

The UtilKit is a small helper package. that can make complex tasks easier.

By offering easy tools to speed up you development.
It offers you SCSS functions and mixins.
And utility-class builder that is super small compared to other utility class frameworks.

<details><summary>Table of Contents</summary>

- [Installation](#installation)
- [How to use](#how-to-use)
  - [Functions](#functions)
  - [Util classes](#util-classes)

</details>

## Installation

```bash
npm install @fylgja/utilkit
```

## How to use

Include the utilkit package in to your code via;

```scss 
@import "@fylgja/utilkit"; // (DartSass, LibSass 3.6)
@import "@fylgja/utilkit/index"; // old way
```

Or just the utilkit classes, via;

```css
@import "@fylgja/utilkit/utilkit.css";
```

There is allot to cover.
So each section is split in it is own file.

### Functions

This contains SCSS functions that extend on base SCSS function like an `str-replace` or an `encode-svg`.
And has some helper mixins to easily build `@media` based styles.

[For more on what each function/mixin does, Check it out here →](https://github.com/fylgja/fylgja-utilkit/wiki/Functions)

### Util classes

The utilkit comes with super strong util class builder and some good defaults.

To use these classes first include the `build-util` mixin.

It is best to load this last after all other css.
This will allows it to override most styles without using an important.

By just calling the `build-util` mixin will also load the default config.
[More on what you are loading and how to configure it here →](https://github.com/fylgja/fylgja-utilkit/wiki/Default-Classes)

If you want more control on what you are loading.

First set the `$utilkit-import` to none.

Second (if not allready done) call the build-util mixin.

And third add your settings to it as found on the [class builder readmore →](https://github.com/fylgja/fylgja-utilkit/wiki/Class-Builder)
