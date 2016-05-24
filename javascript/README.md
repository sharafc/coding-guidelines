# JavaScript Guidelines

A bit more in-depth definition for the JavaScript guidelines.

## Types / Blocks / Comments

### Use the literal syntax for object and array creation.

```javascript
// bad
var object = new Object(); 
var array = new Array();     

// good
var object = {}; 
var array = [];
```

### Use single quotes ' for strings.

```javascript
// bad
var name =  "Max Mustermann" ;
var fullName =  "Max " + lastName;


// good
var name =  'Max Mustermann' ;
var fullName =  'Max '  + lastName;
```

### Use braces for all multi-line blocks.

```javascript
// bad
if (test)
  return false; 
function() { return false; }

// good
if (test) {
  return false;
}
function() {
  return false;
}
```

## Commenting

### Use /** ... */ for multi-line comments and JsDoc.
Include a description, specify types and values for all parameters and return values. This is necessary if you use something like [JsDoc](http://usejsdoc.org/). Even if you are not using it, t it helps to understand the code and many IDEs will interpret the documentation.

```javascript
// bad
// returns a value
// based on the passed in value
function myFunction(e) {
    // do something
    return value;
}

// good
/**
 * returns a value based on the passed in number
 *
 * @param {Integer} number
 * @return {Integer} value
 */
function myFunction(number) {
    //do something
    return value;
}
```

### Use // for single line comments.
Place single line comments on a newline above the subject of the comment. Put an empty line before the comment. 

```javascript
// bad
var active = true;  // is current tab

// good
// is current tab
var active = true;
```

This is in contradiction to Douglas' recommendation, but the best practises changed here. Also Sonar will raise an error if you make same line comments.

 
## Variables / (File)Naming

### Always use var to declare variables.
Not doing so will result in global variable and this is something we clearly dont want.

```javascript
// bad
variable = "Global variable"

// good
var variable = 'Variable in context';
```

### Assign variables at the top of their scope.
This helps avoid issues with variable declaration and assignment hoisting related issues.

```javascript
// bad
function() {
    // doing stuff
    var value = getValue();

    if (value ===  'undefined' ) {
        return false;
    }

    return value;
}

// good
function() {
    var value = getValue();
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



// good
function query() {
  // ..stuff..
}
function changeButtonFont() {}
```

### Use camelCase when naming objects, functions, and instances.

```javascript
// bad
var OBJEcttsssss = {};
var this_is_my_object = {};
var o = {};
function c() {}

// good
var thisIsMyObject = {};
function thisIsMyFunction() {}
```

### Use PascalCase when naming constructors or classes.

```javascript
// bad
var bad = new user({
  name:  'nope' 
});

// good
var good = new User({
  name:  'yup' 
});
```

### Use . (dot) separator combined with lowercase when naming files and namespaces.

```javascript
// bad
// file name moduleUser.js
var moduleUser = function () {
    var method1 = function() {   
        // ...stuff...
    }
    // ...stuff...
};


// good
// file name modules.user.js
modules = modules || {};
modules.User = function () {
   var method1 = function() { 
    // ...stuff...
   }
   // ...stuff...
};
```

### Use $ notation for jQuery objects
```javascript
//bad 
var myObject = $('myDOMElem');

//good
var $myObject = $('myDOMElem');
```

## Comparators

Use === and !== over == and !=.

Conditional statements such as the if statement evaluate their expression using coercion with the ToBoolean abstract method and always follow these simple rules:

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


// good
if (value) {
    // ...stuff...
} 
if (array.length) {
    // ...stuff...
}
```