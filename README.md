# Coding Guidelines

My preferred coding guidelines while implementing stuff.

## Table of Contents

 - [CSS](css/)
 - [JavaScript](javascript/)

## Some general rules

* The basic indentation is four spaces. Tabs are not to be used at all.
* Code is documentation. Comments are useful but should be removed by the delivering system (e.g. minify/uglify)
* Prevent inline styles where possible. The only reasonable way is when changing styling by JavaScript
* Deprecated markup/functionality should never be used

### HTML

The general standard is [HTML5](http://www.w3.org/TR/html5/) from W3C. A short comparison of the rules expanding the W3C rule set follows below.

**Notation**

 * No layout tables. Tables only for their appropriate usage
 * Positioning of page elements only by CSS. No usage of blank gifs or the like
 * Write stringent code. For same page elements use the same containers and tags
 * Tags and attributes have to be written in lowercase
 * Always quote with double quotes (e.g. `<a href=””` )
 * standard attributes will never be explicitly written
 * all necessary attributes have to be filled with usable content (e.g. alt/title)

### CSS

The general standard is [CSS](http://www.w3.org/TR/CSS2/syndata.html) from W3C.

**Notation**

 * The first letter of a class name is always lowercase, logical parts are separated by a dash, e.g. border-blue
 * Attributes have to be written in alphabetical order, starting with mixins
 * Color-codes have to be written hexadecimal and letters everything in lowercase (short form is appreciated)
 * Browser hacks are only allowed if really necessary  (e.g.. box model bug in IE6) most should be handled by a normalize style
 * CSS never replaces semantic (e.g. `<span class=”strong”>` never replaces `<strong>`)
 * Don’t use asterisk comments, they cause errors in less4J
 * Use IDs very carefully

For a more in-depth definition please see the [CSS guidelines](css/).


### JavaScript

The general coding standards are derived from [Mozillas](https://developer.mozilla.org/en-US/docs/Web/JavaScript) coding standards for JavaScript with more specific ruling provided by [Douglas Crockford](http://javascript.crockford.com/code.html).

**Notation**

 * Lines should not contain trailing spaces, even after binary operators, commas or semicolons.
 * Separate binary operators with spaces.
 * Spaces after commas and semicolons, but not before.
 * Spaces after keywords, e.g. if (x > 0).
 * Spaces around braces used for in-line functions or objects, except before commas or semicolons etc. pp.
 * Constants should be in UPPER_CASE
 * Don't use reserved keywords as identifiers, see [ES6](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Lexical_grammar#Reserved_keywords_as_of_ECMAScript_6)

For a more in-depth definition please see the [JavaScript guidelines](javascript/).
