# TypeScript Style Guide

#Incomplete!
* Forked from [https://github.com/Platypi/style_typescript](https://github.com/Platypi/style_typescript)
* Work in progress, do not use yet!

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
* All public functions must have a comment block `/**...*/` using [JSDoc](http://usejsdoc.org/) style comments.

JSDocs can be interpreted by IDEs for better intellisense. Below is an example of a JSDoc comment block for a function.

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

### Class

  * All classes must have block comments `/**...*/` for all public variables and functions.
  * All public functions should use [JSDoc](http://usejsdoc.org/) style comments.
  * Functions need to have a comment explaining what the function does, and all of the input parameters need to be annotated with `@param`.
  * The class should include a block comment containing the description of the class
  * The constructor should contain a JSDoc comment annotating any input parameters.

  ```typescript
  /**
   * Contains properties of a Person.
   */
  class Person {
      /**
       * Returns a new Person with the specified name.
       *
       * @param name The name of the new Person.
       */
      static GetPerson(name: string): Person {
          return new Person(name);
      }

      /**
       * @param name The name of the new Person.
       */
      constructor(public name: string) { }

      /**
       * Instructs this Person to walk for a certain amount
       * of time.
       *
       * @param millis The number of milliseconds the Person
       * should walk.
       */
      walkFor(millis: number) {
          console.log(this.name + ' is now walking.');

          setTimeout(() => {
              console.log(this.name + ' has stopped walking.');
          }, millis);
      }
  }
  ```

### Inline
* Follow the General Standards
* Use `//` for all inline comments.

### Todo and XXX
* Use `// TODO:` to annotate solutions that need to be implemented.
* Use `// XXX:` to annotate problems the need to be fixed.

## Variable Declarations
  * All variables must be declared prior to using them. This aids in code readability and helps prevent undeclared variables from being hoisted onto the global scope.
  * Implied global variables should never be used.
  * You should never define a variable on the global scope from within a smaller scope.
  * Use a `var` keyword to define each variable.
  * Declare each variable on a newline.

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
* Types should be used whenever necessary.
* Arrays should be defined as `type[]` instead of `Array<type>` .
* Use the `any` type sparingly, it is always better to define an interface.
* Always define the return type of functions.
* If TypeScript is capable of implicitly determining the return type of a function, then it is unnecessary to define the return type.
* Always define the types of variables/parameters unless TypeScript can implicitly infer their type.

```typescript
// Like This
var numbers: number[] = [];

// Not Like This
var numbers: Array<number> = [];
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

### Compound

Compound statements are statements containing lists of statements enclosed in curly braces `{}`.

  * The enclosed statements should start on a newline.
  * The enclosed statements should be indented 2 spaces.
  * The left curly brace `{` should be at the end of the line that begins the compound statement.
  * The right curly brace `}` should begin a line and be indented to align with the line containing the left curly brace `{`.
  * **Braces `{}` must be used around all compound statements** even if they are only single-line statements.
  * If you do not add braces `{}` around compound statements, it makes it very easy to accidentally introduce bugs.
  * Compount statements do not need to end in a semicolon `;` with the exception of a `do { } while();` statement.

  ```typescript
  if (condition === true) { alert('Passed!'); }

  if (condition === true) {
      alert('Passed!');
  }

  // Bug may be introduces using this form
  // It appears the intention of the above code is to return if `condition === true`,
  //   but without braces `{}` the return statement will be executed regardless of the condition.
  if (condition === true)
      alert('Passed!');
      return condition;
  ```

### Return

  * If a `return` statement has a value you should not use parenthesis `()` around the value.
  * The return value expression must start on the same line as the `return` keyword.
  * It is recommended to take a return-first approach whenever possible.
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

  * Alway be explicit in your `if` statement conditions.

  ```typescript
  function isString(str: any) {
      return typeof str === 'string';
  }
  ```

Sometimes simply checking falsy/truthy values is fine, but the general approach is to be explicit with what you are looking for. This can prevent a lot of unnecessary bugs.

If statements should take the following form:

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

For statements should have the following form:

  ```typescript
  for(/* initialization */; /* condition */; /* update */) {
      // ...
  }

  ```

### While

While statements should have the following form:

  ```typescript
  while (/* condition */) {
      // ...
  }
  ```

### Do While

  * Do while statements should be avoided unless absolutely necessary to maintain consistency.
  * Do while statements must end with a semicolon `;`

Do while statements should have to following form:

  ```typescript
  do {
      // ...
  } while (/* condition */);
  ```

### Switch

Switch statements should have the following form:

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

  * Each switch group except default should end with `break`, `return`, or `throw`.



### Try

  * Try statements should be avoided whenever possible. They are not a good way of providing flow control.

Try statements should have the following form:

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

  ```typescript
  if (condition) {
      // ...
  }
  ```

  * All operators except for period `.`, left parenthesis `(`, and left bracket `[` should be separated from their operands by a space.

  ```typescript
  var sum = a + b;
  var name = person.name;
  var item = items[4];
  ```

  * No space should separate a unary/incremental operator `!x, -x, +x, ~x, ++x, --x` and its operand.

  ```typescript
  var neg = -a;
  ```

  * Each semicolon `;` in the control part of a `for` statement should be followed with a space.

  ```typescript
  for(var i = 0; i < 10; ++i) {
      // ...
  }
  ```



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
  ``

## === and !== Operators

  * It is better to use `===` and `!==` operators whenever possible.
  * `==` and `!=` operators do type coercion, which can lead to headaches when debugging code.

## Eval

  * **Never use eval**
  * **Never use the Function constructor**
  * **Never pass strings to `setTimeout` or `setInterval`**

## TSLint

  * Always use a Linter

Linting your code is very helpful for preventing minor issues that can escape the eye during development. We use TSLint (written by Palantir) for our linter.

  * TSLint: https://github.com/palantir/tslint
  * Our [tslint.json](https://github.com/Platypi/style_typescript/blob/master/tslint.json)
