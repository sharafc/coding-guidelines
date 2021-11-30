# HTML Guidelines

The general standard is [HTML](https://html.spec.whatwg.org/) from WhatWG. In addition to that I expande the
ruleset as follows:

## General rules

 * No layout tables. Tables only for their appropriate usage
 * Positioning of page elements only by CSS. No usage of blank gifs or the like
 * Write stringent code. For same page elements use the same containers and tags
 * All necessary attributes have to be filled with usable content (e.g. alt/title)
 * Standard attributes will never be explicitly written
 * Write semantic HTML, no div soups
 * Respect A11y, use aria roles where appropriate

## Syntax
 * Do not capitalize tags or attributes
 * Tags and attributes have to be written in lowercase
 * Always quote with double quotes (e.g. `<a href=""`)
 * Do not include a trailing slash in self-closing elements
 * Do not omit optional closing tags

## Meta data

```html
// Bad HTML example
<html>
    <head>
    </head>
    <body>
    </body>
</html>

// Better HTML example
<!doctype html>
<html lang="en">
    <head>
        <meta charset="utf-8">
    </head>
    <body>
    </body>
</html>
```
### HTML doctype
Always define the html doctype at the beginning of ervery html page to enforce standard mode.

### Language attribute
To aid speech analysis tools and screen readers always specify the lang attribute on the root html.

### Character encoding
Ensure proper rendering by declaring an explicit encoding.

### IE compat mode
There should be no need for this anymore since only IE10 and below did support this.

## CSS and JS includes
There usually is no need to specify the `type` attribute when including CSS and JS files. `text/css` and `text/javascript` are the respective defaults and automatically used.

## Boolean attributes
Don't add a value to a boolean attribute.

See the [WhatWG section on boolean attributes](https://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes):
> The presence of a boolean attribute on an element represents the true value, and the absence of the attribute represents the false value.

If there is absolutely no way around, also follow the WhatWG guideline:
>If the attribute is present, its value must either be the empty string or the attribute's canonical name, with no leading or trailing whitespace.
