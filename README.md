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

1. Sublime Text
2. Vi or (Vi IMproved)

Use tools like `js-beautify` to automatically format your code as configured. Run it with git pre-commit hook to make sure all your committed code is always formatted.

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

`engines` is a container for all kinds of engines

`petrolEngines` contains a subset of engines whose fuel is petrol

`dieselEngines` contains a subset of engines whose fuel is diesel


#### Functions
Function names should convey some action like verbs.

`run()`

`captureStream()`

`checkInCache()`

Function names should give a hint of the return type

```
isValid()           // true/false

canContinue()       // true/false

getUsers()          // array of objects

getFriendCount()    // number
```

#### Constructors
#### Constants
#### Objects

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

## Casing
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

### Errors
Always create a new Error object with your message. Don't just return a string message to the callback. Stack traces are handy.

## Markup

## Styles

## Attribution

NPM's "funny" coding style
