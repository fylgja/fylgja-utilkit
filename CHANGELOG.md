# Changelog

## 2.3.0 - (2020-04-18)
* IMP: move docs to wiki
* ADD:
  * function map-deep-merge
  * option to quickly set the important value to the properties,
    display margin and padding

## 2.2.0 - (2019-12-06)
* FIX: `@media` classes overriding util classes, [Issue#1](https://github.com/fylgja/fylgja-utilkit/issues/1)
* IMP: `loop-mq()` function can now exclude **xs** styles

## 2.1.0 - (2019-10-02)
* IMP:
  * allow loading of each util pack separately.
  * Don't load classes until called via `build-util`

## 2.0.2 - (2019-09-08)
* FIX: importer loading all even if only text is set

## 2.0.1 - (2019-08-31)
* FIX: allow imports for older sass versions
  * will dropped in the future (https://github.com/sass/node-sass/issues/2111)

## 2.0.0 - (2019-08-31)
* IMP:
  * Rebuild folder structure for easier management
  * Split doc in parts for each util
* ADD: More complete default util classes

## 1.0.3 - (2019-08-09)
* FIX:
  * flex-shrink default util class
  * typo in Readme

## 1.0.1 - (2019-07-31)
* Initial release 🎉
