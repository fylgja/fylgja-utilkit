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
  - [Util classes builder](#util-classes-builder)

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

[For more on what each function/mixin does, Check it out here →](functions/README.md)

### Util classes

This contains the documentation on what is in the box by default.
And how to use these CSS classes.

[Check it out here →](classes/README.md)

### Util classes builder

How to use build your own **util classes**, via the builder.

[Check it out here →](class-builder/README.md)
