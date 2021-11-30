# Coding Guidelines

Best practices and guidelines for writing HTML, CSS , JavaScript and other languages.

> Every line of code should appear to be written by a single person, no matter the number of contributors.
*Twitter*

## Table of Contents

 - [HTML](html/)
 - [CSS](css/)
 - [JavaScript](javascript/)

### Source Code Formatting

The following settings are required for source code created within the project(s). The recommendation is to set the
configuration of IDE settings accordingly.

|    Type      |     Setting    |
|--------------|----------------|
| Line Width   | 120 characters |
| Indention    | 4 spaces       |
| Encoding     | UTF-8          |
| Line Endings | UNIX           |

* Tabs are not to be used at all, use soft tabs with 4 spaces
* Code is documentation. Comments are useful, but should be removed by the delivering system (e.g. minify/uglify)
* Prevent inline styles where possible. The only reasonable way is when changing styling by JavaScript
* Deprecated markup/functionality should never be used
* Add new line at end of files
* Trim trailing white space

### JavaScript

The general coding standards are derived from [Mozillas](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
coding standards for JavaScript with more specific ruling provided by
[Douglas Crockford](http://javascript.crockford.com/code.html). Also the Coding Guidelines from
[AirBnb](https://github.com/airbnb/javascript) are pretty awesome.

**Notation**

 * Lines should not contain trailing spaces, even after binary operators, commas or semicolons
 * Separate binary operators with spaces
 * Spaces after commas and semicolons, but not before.
 * Spaces after keywords, e.g. if (x > 0)
 * Spaces around braces used for in-line functions or objects, except before commas or semicolons etc. pp.
 * Constants should be in UPPER_CASE
 * Don't use reserved keywords as identifiers, see
[ES6](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#keywords)

For a more in-depth definition please see the [JavaScript guidelines](javascript/).

#### JSDoc

Every method needs to get a JSDoc comment. The comment should describe the meaning and the responsibility of the class
or the method. It is important that responses to null values or similar values that may be out of range are described.
Also parameters must be documented and explained.
