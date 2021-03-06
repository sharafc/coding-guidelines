# CSS/LESS Guidelines

A bit more in-depth definition for the CSS/Less guidelines.

## File naming
Typically you should create CSS modules and a namespace for your library. The file naming should follow this structure.
As divider we us the underscore `_`:
```
<namespace>_<modulename>_<submodulename>.less/.css
```

## Formatting / Blocks / Comments

 * Use dashes over camelCasing in class names. 
 * When using multiple selectors in a rule declaration, give each selector its own line.
 * Put a space before the opening brace { in rule declarations
 * In properties, put a space after, but not before, the : character.
 * Put closing braces } of rule declarations on a new line
 * Put blank lines between rule declarations if they don't belong together

```css
// bad
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}

// good
.avatar {
  border: 2px solid white;
  border-radius: 50%;
}

.one,
.selector,
.per-line {
  // ...
}
```

## Comments

 * Prefer line comments (// in less) to block comments. Do not use asterisk comments (/* ... */) because they cause
errors in [Less4J](https://github.com/SomMeri/less4j/).
 * Prefer comments on their own line. Avoid end-of-line comments.
 * Write detailed comments for code that isn't self-documenting:
    - Uses of z-index
    - Compatibility or browser-specific hacks
    - Overwriting of framework styles
 * Avoid specificity hell as much as possible.


## Write styles mobile-first

Since websites should be in a responsive layout, our mobile styling should always be the basic/fallback for all browser
who cannot deal with media queries. Therefore the basic layout is always the mobile one and has to be declared without
media queries.

```css
// bad
@media screen and (max-width: @smallest-screen) {
    // my styles
}
@media screen and (min-width: @medium-screen) {
   // my tablet styles 
}
@media screen and (min-width: @big-screen) {
   // my desktop styles 
}

// good
// my basic styles

@media screen and (min-width: @medium-screen) {
   // my tablet styles 
}

@media screen and (min-width: @big-screen) {
   // my desktop styles 
}
```

## ID as selectors for HTML elements

Cascade and Specificity are a major point at style development. A strict and transparent development reduces maintenance
time. IDs should only be carefully used to avoid the feared ID soup. This can also prevent
[specificity hell](https://www.smashingmagazine.com/2010/04/css-specificity-and-inheritance/). If in doubt you can also
[calculate the specificity](https://specificity.keegan.st/)

 * IDs must be explicit.
 * IDs raise the specificity of a class.
 * IDs are a possibility to capsulate CSS classes but should be used very careful. Best is to use them only for
JavaScript hooks.


## Variables / Mixins

### Define colors and values in variables

Quite self-explanatory. Every color has to be defined in the theme variables. All have to be bundled together.

```css
LESS

    @color-white:   #fff;
    @color-black:   #000;
    @brand-success: #41a500;

CSS

    p {
        color: @color-black;
    }

    div {
        background-color: @color-white;
        &.success {
            background-color: @brand-success;
        }
    }
```

### Use mixins sparingly

Mixins without a parameter are most of the time not needed because they just produce overhead. The only reason to do
that is, if you have some defined fallback which you have to overwrite (but then you have at least in the definition of
the mixin a parameter).

```css
// bad
.text-all-caps() {
    text-transform: uppercase;
}

//good
.text-transformation(@text-transformation: uppercase) { 
    text-transform: @text-transformation;
}
```

### Don't use @extend

Never. Just don't. If you want to read more about it, you can find some information in this nice article from
[CSS Wizardry](http://csswizardry.com/2016/02/mixins-better-for-performance/). It handles Sass, but the result is the
same.
