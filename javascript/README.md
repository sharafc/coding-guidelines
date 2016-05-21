# JavaScript Guidelines

A bit more in-depth definition for the JavaScript guidelines.


## Types / Blocks / Comments

### Use the literal syntax for object and array creation.

```javascript
// bad
var item = new Object(); 
var items = new Array();     

// good
var item = {}; 
var items = [];
```

### Use single quotes '' for strings.

```javascript
// bad
var name =  "Bob Parr" ;
var fullName =  "Bob "  + this.lastName;


// good
var name =  'Bob Parr' ;
var fullName =  'Bob '  + this.lastName;
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
Include a description, specify types and values for all parameters and return values. This is necessary if you use something like [JsDoc](http://usejsdoc.org/). Even if not it helps to understand the code and many IDEs will interpret the documentation.

```javascript
// bad
// returns a new element
// based on the passed in tag name
function make(tag) {
  return element;
}

// good
/**
 * returns a new element based on the passed in tag name
 *
 * @param {String} tag
 * @return {Element} element
 */
function make(tag) {
  return element;
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

 
## Variables / Naming

### Always use var to declare variables.
Not doing so will result in global variables. We want to avoid polluting the global namespace.

```javascript
// bad
superPower = new SuperPower();        

// good
var superPower = new SuperPower();
```

### Assign variables at the top of their scope.
This helps avoid issues with variable declaration and assignment hoisting related issues.

```javascript
// bad
function() {
  // doing stuff
  var name = getName();

  if (name ===  'test' ) {
    return false;
  }

  return name;
}

// good
function() {
  var name = getName();
  // doing stuff

  if (name ===  'test' ) {
    return false;
  }

  return name;
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
if (name !==  ' ' ) {
  // ...stuff...
}
if (collection.length > 0) {
  // ...stuff...
}


// good
if (name) {
  // ...stuff...
} 
if (collection.length) {
  // ...stuff...
}
```