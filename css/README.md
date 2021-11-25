# CSS Guidelines

The general standard is [CSS](https://www.w3.org/Style/CSS/) from W3C.

## General rules

  * CSS never replaces semantic (e.g. `<span class=”strong”>` never replaces `<strong>`)
  * Prefer dashes over camelCasing in class names
    * Underscores and PascalCasing are okay and needed if you are using BEM
  * Attributes have to be written in alphabetical order, starting with mixins
  * Put a space before the opening brace `{` in rule declarations
  * Put closing braces `}` of rule declarations on a new line
  * End all declarations with a `;`
  * Include one space after, but not before, the `:` for each declaration
  * When using multiple selectors in a rule declaration, give each selector its own line.
  * Include one space after each comma of the property list
  * Lowercase all attributes and use shorthand notation
  * Avoid unit declarations for zero values
  * Quote attribute values in selectors with a double quote
  * Put blank lines between rule declarations if they don't belong together

```css
// Bad CSS examples
.myAwesomeClass{
    border-radius:50%;
    border:2px solid white; }
.na, .niet, .no_no {
    // ...
}
#yolo {
  margin :0px;
  color: #AFAFAF
}
.selector[type=text] {
    // ...
}

// Good CSS examples
.MyAwesomeComponent,
.my-awesome-class {
  border: 2px solid #fff;
  border-radius: 50%;
  color: #afafaf;
  margin: 0;
}

.only-one,
.selector,
.per-line {
  // ...
}

.selector[type="text"] {
    // ...
}
```

## ITCSS and BEM
CSS should not just float around but should, like other software components, have a clean and understandable architecture.
Therefore I love to combine the structural benefits of ITCSS with a bit of SMACSS and the rules of BEM.
Combined with a pre-processor like SASS it becomes nearly a no-brainer.
For a bit more information about my personal architecture choice, you can read my blog post about [CSS Architecture](https://www.christian-sharaf.de/blog/2021/css-architecture-decisions/).

Following this structure helps us with a modular (or component) driven approach to CSS and less bloat and overwriting in our styles.
```html
<article class="article article--hero">
    <h1 class="article__title">Awesome Title</h1>
    <div class="article__content">
        <p>Lorem ipsum etc. pp.</p>
    </div>
</article>
```

```css
.article {
    &--hero {}
    &__title {}
    &__content {}
}
```

## Do not use @import
Just don't.
For more information, read this article by [Steve Souders](https://www.stevesouders.com/blog/2009/04/09/dont-use-import/).


## Do not use @extend
Never. Just don't.
If you want to read more about it, you can find some information in this nice article from [CSS Wizardry](http://csswizardry.com/2016/02/mixins-better-for-performance/). It handles Sass, but the result is the same.

## File naming
Typically you should create CSS modules and a namespace for your library. The file naming should follow this structure.
As divider we us the underscore `_`:
```
<namespace>_<modulename>_<submodulename>.less/.css
```

## Comments
Good code comments provide context or purpose and do not just repeat component or class names.

 * Prefer comments on their own line. Avoid end-of-line comments.
 * Write detailed comments for code that isn't self-documenting, e.g.:
    - Uses of z-index
    - Compatibility or browser-specific hacks
    - Overwriting of framework styles


## Write styles mobile-first
Since websites should be in a responsive layout, mobile styling should always be the basic/fallback for all browser who cannot deal with media queries. Therefore the basic layout is always the mobile one and has to be declared without media queries.

```css
// Bad Query example
@media screen and (max-width: @smallest-screen) {
    // basic styles
}
@media screen and (min-width: @medium-screen) {
   // tablet styles
}
@media screen and (min-width: @big-screen) {
   // desktop styles
}

// Better Query example
// generic styles
p {
    font-size: 1.5rem;
}
@media screen and (min-width: @medium-screen) {
    // tablet styles
    p {
        font-size: 1.2rem;
    }
}

@media screen and (min-width: @big-screen) {
    // desktop styles
    p {
        font-size: 1rem;
    }
}
```

## ID as selectors for HTML elements

Cascade and Specificity are a major point at style development. A strict and transparent development reduces maintenance time. IDs should only be carefully used to avoid the feared ID soup. This can also prevent [specificity hell](https://www.smashingmagazine.com/2010/04/css-specificity-and-inheritance/). If in doubt you can also [calculate the specificity](https://specificity.keegan.st/)

 * IDs must be explicit.
 * IDs raise the specificity of a class.
 * IDs are a possibility to capsulate CSS classes but should be used very careful. Best is to use them only for
JavaScript hooks.


## Variables / Mixins

### Define colors and values in variables

Quite self-explanatory. Every color has to be defined in the theme variables. All have to be bundled together.

```css
SASS

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

Mixins without a parameter are most of the time not needed because they just produce overhead. The only reason to do that is, if you have some defined fallback which you have to overwrite (but then you have at least in the definition of the mixin a parameter).

```css
// bad
.text-all-caps() {
    text-transform: uppercase;
}

// better
.text-transformation(@text-transformation: uppercase) {
    text-transform: @text-transformation;
}
```
