# Development Guidelines for Web

Developing for Web usually means to jostle between a number of languages, markups, stylesheets and disparate syntaxes. This guide intends to bring all the usual paradigms and best practices under one hood.

This is a living document and each point is open for discussion & debate. Feel free to add issues or fork, make changes & send pull requests.

Covering everything is not possible. When in doubt,

__K I S S__

`Keep It Short and Simple`

## Indentation
Use 2 spaces. Configure your editor to automatically convert tabs to spaces.

* Takes less space
* Looks correct when copied and pasted on other text editors or Github
* Tabs are inconsistent

How to configure your editor:

1. [Sublime Text](https://github.com/vxtindia/web-style-guide/wiki/Editor-Configuration#sublime-text)
2. [Vi or (Vi IMproved)](https://github.com/vxtindia/web-style-guide/wiki/Editor-Configuration#vi)

Use tools like [js-beautify](https://github.com/einars/js-beautify) to automatically format your code as configured. Run it with git pre-commit hook to make sure all your committed code is always formatted.

## Line Length
Try to fit your lines in 80 characters. This prevents horizontal scrolling and makes the code clean & more readable. Editors usually show the column number in status bars. If you are using Submile Text, add `"rulers": [80]` in your preferences file to mark the 80'th column.

_Long line_

```javascript
picker.setDate(new Date(date.getFullYear(), date.getMonth(), date.getDate() + 1));
```

_80 Columns_

```javascript
picker
  .setDate(new Date(
    date.getFullYear(),
    date.getMonth(),
    date.getDate() + 1)
  );
```

__Note: Ignore this rule when writing markups as they are heavily indented.__


## JavaScript

### Identifier Naming

> There are only two hard things in Computer Science: cache invalidation and naming things - _Phil Karlton_

Anything that is not a reserved keyword are identifiers.

#### Variables
Variable names should be short & nice English words. Always create a connection between variable names & business logic. Name them in such a way that your grandmother can understand too.


_Examples_

If your software brews coffee, use an apt name

`brew` or `brewCoffee`

Don't use variable names that only programmers can understand like `str` or `char` or `data` or `dbResults`. Instead the name should say what kind of data it expects, like `comment` or `rating` or `likes` or `products`

Give specific names when the sitation demands so, like:

```javascript
var engines;        // container for all kinds of engines
var petrolEngines;  // container for a subset of engines that gulp petrol
var dieselEngines;  // container for a subset of engines that gulp diesel
```

#### Functions
Function names should convey some action like verbs.

```javascript
run();
captureStream();
checkInCache();
```

Function names should give a hint of the return type

```javascript
isValid()           // true/false
canContinue()       // true/false
getUsers()          // array of objects
getFriendCount()    // number
```

#### Constructors
#### Constants
#### Objects
#### Public & Private variables
Follow the usual variable naming convention for local variables of a class. When using CommonJS (node.js), to make whatever objects/primitives public, just attach them to the exports object (or module.exports). No need to use `_` for denoting private variables.

```javascript
var fs = require('fs');

// Public method
// Whoever is reading this code can easily identify this as a public method
// as this is being attached to the exports object
exports.exists = function(path) {
    return pathExists(path);
};


// Private method
// Automtically becomes private as this is not under the exports namespace
// Will not be accessible outside of this module
function pathExists() {
    return fs.existsSync(path);
}
```

When using AMD (require.js), to make whatever objects/primitives public, just return those from the function

```javascript
require(['user'], function(User) {

    // Remains private
    var users = [];

    function addUser(name) {
        var user = new User(name);
        users.push(user);
    }

    function getUserCount() {
        return users.length;
    }

    // Maintain your public/private relationships nicely
    return {
        addUser: addUser,
        getUserCount: getUserCount
    };
});
```

### Declaration
If assigning, declare each variable in its own line

Bad

```javascript
var foo = ['code', 'quality', 'matters'], bar = '!';
var baz, caz;
```

Good

```javascript
var foo = ['code', 'quality', 'matters'];
var bar = '!';
var baz, caz;
```

Boolean variables and functions should always be either true or false. Don't set it to 0 unless it's supposed to be a number.

When something is intentionally missing or removed, set it to null.

Don't set things to undefined. Reserve that value to mean "not yet set to anything."

### Literal Syntax

Always use literal syntax to allocate Objects, Arrays, Booleans, Strings

Bad

```javascript
var foo = new Array();
var bar = new Boolean(true);
var baz = new Object();
var caz = new RegExp(/\d/);
```

Good
```javascript
var foo = [];
var bar = true;
var baz = {};
var caz = /\d/;
```

__Note: new Date() is fine__

### Casing
Use `lowerCamelCase` for multiword identifiers when they refer to objects, functions, methods, members, or anything not specified in this section.

Use `UpperCamelCase` for class names (things that you'd pass to "new").

Use `all-lower-hyphen-css-case` for multiword filenames and config keys.

Use `CAPS_SNAKE_CASE` for constants, things that should never change and are rarely used.

Use a single uppercase letter for function names where the function would normally be anonymous, but needs to call itself recursively. It makes it clear that it's a "throwaway" function.

### Braces

Bad

```javascript
function foo()
{
    // Bla bla
}
```

Good

```javascript
function foo() {
    // Bla bla
}
```

If a block needs to wrap to the next line, use a curly brace. Don't use it if it doesn't.

Bad

```javascript
if (foo) { bar() }
while (foo)
    bar()
```

Good

```javascript
if (foo) bar()
while (foo) {
    bar();
}
```

### Whitespace

Put a single space in front of ( for anything other than a function call. Also use a single space wherever it makes things more readable.

Don't leave trailing whitespace at the end of lines. Don't indent empty lines. Don't use more spaces than are helpful.

Bad
```javascript
if(foo){
    //do foo
}
```

Good
```javascript
if (foo) {
    // doo foo
}
```

Bad

```javascript
var grandTotal=total+taxes;
```

Good

```javascript
var grandTotal = total + taxes;
```

### Named Functions
Name your anonymous functions. They make stack traces a lot easier to read.

Bad

```javascript
setTimeout(function() {
    foo();
}, 1000);
```

Good
```javascript
setTimeout(function doFoo() {
    foo();
}, 1000);
```

### Semicolons / ASI

### Magic Numbers
[What is a Magic Number? Why is it bad?](http://stackoverflow.com/questions/47882/what-is-a-magic-number-and-why-is-it-bad)

### Errors
Always create a new Error object with your message. Don't just return a string message to the callback. Stack traces are handy.

## Markup

## Styles

## Attributions ©

[NPM's "funny" coding style](https://npmjs.org/doc/coding-style.html)
