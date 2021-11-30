# JavaScript Guidelines


:boom::fire: This part is outdated and needs a big overhaul. :fire::boom:

A bit more in-depth definition for the JavaScript guidelines.

## Types / Blocks / Comments

### Use the literal syntax for object and array creation.

```javascript
// bad
let object = new Object();
let array = new Array();

// better
let object = {};
let array = [];
```

While there is no performance difference, the literal syntax is more concise. Also the `Array` constructor has the single-argument pitfall, therefore it should be avoided.

### Use single quotes `''` for strings.

```javascript
// bad
let name =  "Max Mustermann";
let fullName =  "Max " + lastName;

// better
let name =  'Max Mustermann';
let fullName =  'Max '  + lastName;
```

### Use braces `{}` for all multi-line blocks.

```javascript
// bad
if (test)
  return false;
function() { return false; }

// better
if (test) {
  return false;
}
function myFunction () {
  return false;
}
```

## Commenting

### Use `/** ... */` for multi-line comments and JsDoc.
Include a description, specify types and values for all parameters and return values. This is necessary if you use
something like [JsDoc](http://usejsdoc.org/). Even if you are not using it, t it helps to understand the code and many
IDEs will interpret the documentation.

```javascript
// bad
// returns a value
// based on the passed in value
function myFunction(e) {
    // do something
    return value;
}

// better
/**
 * returns a value based on the passed in number
 *
 * @param {Integer} number The number you want to modify
 * @return {Integer} value The modified value
 */
function myFunction(number) {
    //do something
    return value;
}
```

### Use `//` for single line comments.
Place single line comments on a newline above the subject of the comment. Put an empty line before the comment.

```javascript
// bad
let active = true;  // is current tab

// better
// is current tab
let active = true;
```

This is in contradiction to Douglas' recommendation, but the best practises changed here. Also Sonar will raise an error
if you make same line comments.


## Variables / (File)Naming

### Always use `let` to declare variables.
Not doing so will result in global variable and this is something we clearly dont want.

```javascript
// bad
variable = "Global variable"

// better
let variable = 'Variable in context';
```

### Assign variables at the top of their scope.
This helps avoid issues with variable declaration and assignment hoisting related issues. Also it could prevent the [Temporal Dead Zone](https://www.christian-sharaf.de/blog/2020/temporal-dead-zone/).

```javascript
// bad
function() {
    // doing stuff
    let value = getValue();

    if (value ===  'undefined' ) {
        return false;
    }

    return value;
}

// better
function() {
    let value = getValue();
    // doing stuff
    if (value ===  'undefined' ) {
        return false;
    }

    return value;
}
```

### Avoid single letter/non-speaking names.
Be descriptive with your naming. We don't have to save characters like in the early days.

```javascript
// bad
function q() {
  // ...stuff...
}
function chgBtnFnt() {}



// better
function query() {
  // ..stuff..
}
function changeButtonFont() {}
```

### Use camelCase when naming objects, functions, and instances.

```javascript
// bad
let OBJEcttsssss = {};
let this_is_my_object = {};
let o = {};
function c() {}

// better
let thisIsMyObject = {};
function thisIsMyFunction() {}
```

### Use PascalCase when naming constructors or classes.

```javascript
// bad
let bad = new user({
  name:  'nope'
});

// better
let good = new User({
  name:  'yup'
});
```

### Use `.` (dot) separator combined with lowercase when naming files and namespaces.

```javascript
// bad
// file name moduleUser.js
let moduleUser = function () {
    let method1 = function() {
        // ...stuff...
    }
    // ...stuff...
};


// better
// file name modules.user.js
modules = modules || {};
modules.User = function () {
   let method1 = function() {
    // ...stuff...
   }
   // ...stuff...
};
```

### Use `$` notation for jQuery objects
```javascript
//bad
let myObject = $('myDOMElem');

//good
let $myObject = $('myDOMElem');
```

## Comparators

Use `===` and `!==` over `==` and `!=`.

Conditional statements such as the if statement evaluate their expression using coercion with the ToBoolean abstract
method and always follow these simple rules:

 * Objects evaluate to true
 * Undefined evaluates to false
 * Null evaluates to false
 * Booleans evaluate to the value of the boolean
 * Numbers evaluate to false if +0, -0, or NaN, otherwise true
 * Strings evaluate to false if an empty string '', otherwise true

### Use shortcuts when possible.
```javascript
// bad
if (value !==  ' ' ) {
    // ...stuff...
}
if (array.length > 0) {
    // ...stuff...
}


// better
if (value) {
    // ...stuff...
}
if (array.length) {
    // ...stuff...
}
```