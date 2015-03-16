# TypeScript Style Guide

#Incomplete!
* Forked from [https://github.com/Platypi/style_typescript](https://github.com/Platypi/style_typescript)
* Work in progress, do not use yet!

## Recommended Visual Studio Add-In
* [Web Essentials](http://vswebessentials.com/download)
* [Code Alignment](http://www.codealignment.com/)

## Coding Standards
* All file shoule follow the general coding standards unless specificly stated here

## Indentation
* The unit of indentation is 2 spaces.
* **Never use tabs**, as this can lead to trouble when opening files in different IDEs/Text editors. Most text editors have a configuration option to change tabs to spaces.

## Quotes
* Use double-quotes `""` for all strings, and use single-quotes `''` for strings within strings.
* This is to stay consistent with other languages that do not use signel quotes

```typescript
var greeting = "Hello World!";
var html = "<div class='bold'>Hello World</div>";
```

## Comments
* Follow the General Coding Standards
* It is recommened that classes and fucntions should have a comment block `/**...*/` using [JSDoc](http://usejsdoc.org/) style comments.
* Functions should have a comment explaining what the function does and what all of the input parameters are/do.
* Classes should include a block comment containing the description of the class

_JSDocs can be interpreted by IDEs for better intellisense. Below is an example of a JSDoc comment block for a function._

  ```typescript
  /**
   * Takes in a name and returns a greeting string.
   *
   * @param name The name of the greeted person.
   */
  function getGreeting(name: string): string {
      return 'Hello ' + name + '!';
  }
  ```

## Variable Declarations
  * All variables must be declared prior to using them. Use a `var` keyword to define each variable.
  * Global and Implied global variables should never be used.
  * Declare each variable on a newline.

_Proper variable decclarations aids in code readability and helps prevent undeclared variables from being hoisted onto the global scope._

  ```typescript
  // Like This
  var a = 2;
  var b = 2;
  var c = 4;

  // Not Like These
  // ------------------------------------------------------
  var a = 2,
      b = 2,
      c = 4;

  // b will be defined on global scope.
  var a = b = 2, c = 4;

  function add(a: number, b: number) {
      // c is on the global scope!
      c = 6;

      return a + b + c;
  }
  ```

## Function Declarations
* Follow the General Standard.
* There should be no space between the parameter and the colon `:` indicating the type declaration.
* There should be a space between the colon `:` and the type declaration.

```typescript
// Standard Function Syntax
function foo(param1: type, param2: type): returnType {
    return 'foo';
}

// Example of returning a function
function bar(name: string): string {
    var message = "Hello ;

    function greet() {
        return message + name + "!";
    }
    return greet;
}

// Example of returning an object
function foorbar(name: string): string {
    var message = "Hello ";

    var foobar = {
      greet: function(name: string) => {
          return message + name + "!";
        }
    };
    return foobar;
}
```

### Anonymous Functions
* All anonymous functions should be defined as fat-arrow/lambda `() => { }` functions unless it is absolutely necessary to preserve the context in the function body.
* All fat-arrow/lambda functions should have parenthesis `()` around the function parameters.
* There should be a space between the right parenthesis `)` and the `=>`
* There should be a space between the `=>` and the left curly brace `{` that begins the statement body.
* The statement body should be indented like a normal function.
* The right curly brace `}` should be on a new line.
* The right curly brace `}` should be aligned with the line containing the  left curly brace `{` that begins the function statement.

```typescript
element.addEventListener('click', (ev: Event) => { alert('foo'); });

element.addEventListener('click', (ev: Event) => {
    alert('foo');
});
```



## Names
* Follow the General Standard.

### Types
* Types should always be used. The use of type `any` should only be used sparingly, it is better to define an interface.
* Arrays should be defined as `type[]` instead of `Array<type>` .
* Always define the return type of functions.

```typescript
// Like This
var itemIndex: number;
var greeting: string = "Hello World"; 
var numbers: number[] = [];
```

### Classes
```typescript
// Example class definition
class Person {
    private _fullName: string;

    constructor(public firstName: string, public lastName: string) {
        this._fullName = firstName + ' ' + lastName;
    }
    
    public toString() {
        return this.__fullName;
    }

    private _walkFor(millis: number) {
        console.log(this._fullName + ' is now walking.');

        // Wait for millis milliseconds to stop walking
        setTimeout(() => {
            console.log(this._fullName + ' has stopped walking.');
        }, millis);
    }
}
```

## Statements
### Simple
* Each line should contain at most one statement.
* A semicolon should be placed at the end of every simple statement.

### Return
* Always **explicitly define a return type**. This can help TypeScript validate that you are always returning something that matches the correct type.

```typescript
function getHighestNumber(a: number, b: number): number {
    if(a >= b) {
        return a;
    }
    return b;
}
```


### If
_If statements should take the following form:_

```typescript
if (/* condition */) {
    // ...
}

if (/* condition */) {
    // ...
} else {
    // ...
}

if (/* condition */) {
    // ...
} else if (/* condition */) {
    // ...
} else {
    // ...
}
```

### For
_For statements should have the following form:_

```typescript
for(/* initialization */; /* condition */; /* update */) {
    // ...
}
```

### While

_While statements should have the following form:_

```typescript
while (/* condition */) {
    // ...
}
```

### Do While
* Do while statements should be avoided unless absolutely necessary to maintain consistency.
* Do while statements must end with a semicolon `;`

_Do while statements should have to following form:_

```typescript
do {
    // ...
} while (/* condition */);
```

### Switch
* Each switch group except default should end with `break`, `return`, or `throw`.

_Switch statements should have the following form:_

```typescript
// Single Statement in Each Case
switch (/* expression */) {
    case /* expression */: /*Statement*/;  /* termination */;
    case /* expression */: /*Statement*/;  /* termination */;
    case /* expression */: /*Statement*/;  /* termination */;
    default:
        // ...
}

// Multiple Statement in Each Case
switch (/* expression */) {
    case /* expression */:
        // ...
        /* termination */
    case /* expression */:
        // ...
        /* termination */
    default:
        // ...
}
```

### Try
* Try statements should be avoided whenever possible. They are not a good way of providing flow control.

_Try statements should have the following form:_
```typescript
try {
    // ...
} catch (error: Error) {
    // ...
}

try {
    // ...
} catch (error: Error) {
    // ...
} finally {
    // ...
}
```

### Continue
* It is recommended to take a continue-first approach in all loops.

### Throw
* Avoid the use of the throw statement unless absolutely necessary.
* Flow control through try/catch exception handling is not recommended.

## Whitespace
Blank lines improve code readability by allowing the developer to logically group code blocks. Blank spaces should be used in the following circumstances.

  * A keyword followed by left parenthesis `(` should be separated by 1 space.
  * All operators except for period `.`, left parenthesis `(`, and left bracket `[` should be separated from their operands by a space.
  * No space should separate a unary/incremental operator `!x, -x, +x, ~x, ++x, --x, x++, x--` and its operand.
  * Each semicolon `;` in the control part of a `for` statement should be followed with a space.

## Object and Array Literals
  * Use curly braces `{}` instead of `new Object()`.
  * Use brackets `[]` instead of `new Array()`.

## Assignment Expressions
  * Assignment expressions inside of the condition block of `if`, `while`, and `do while` statements should be avoided.

```typescript
// Like This
while (typeof node === 'object') {
    node = node.next;
    // ...
}

// Not Like This
while (node = node.next) {
    // ...
}
```

## === and !== Operators
* It is better to use `===` and `!==` operators whenever possible.
* `==` and `!=` operators do type coercion, which can lead to headaches when debugging code.

## Eval
* **Never use eval**
* **Never use the Function constructor**
* **Never pass strings to `setTimeout` or `setInterval`**

## TSLint
* Always use a Linter. The Web Essentials VS AddIn come with one. 
* Use the `tslint.json` file in the reposisotry to help keep all code consistent.

Linting your code is very helpful for preventing minor issues that can escape the eye during development. 
