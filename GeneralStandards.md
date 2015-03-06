
## Introduction
When developing software as an organization, the value of the software produced is directly affected by the quality of the codebase. Consider a project that is developed over many years and handled/seen by many different people. If the project uses a consistent coding convention it is easier for new developers to read, preventing a lot of time/frustration spent figuring out the structure and characteristics of the code. For that purpose, we need to make sure we adhere to the same coding conventions across all of our products. This will not only help new developers, but it will also aid in quickly identifying potential flaws in the code, thereby reducing the brittleness of the code.



## Browser Compatibility
* Target modern browsers `ie >= 9`.

## Files
* Files must have the proper extension for the filetype.
* All files should end in a new line. This is necessary for some Unix systems.
* Filename should separate words with either periods or camelCase (e.g. `my.view.html` or `myView.html`).

## Line Length
* Lines must not be longer than 140 characters.
* When a statement runs over 140 characters on a line, it should be broken up, ideally after a comma or operator.

## Comments
* Comments are strongly encouraged. It is very useful to be able to read comments and understand the intentions of a given block of code.
* Comments need to be clear, just like the code they are annotating.
* Make sure your comments are meaningful.
* Preference would be given to good variable names and clean code over comments.

The following example is a case where a comment is completely erroneous, and can actually make the code harder to read.

```
// Set index to zero.
var index = 0;
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
* Inline comments are comments inside of complex statements (loops, functions, etc).
* Use `//` (or symbols depending on language) for all inline comments.
* Keep comments clear and concise.
* Place inline comments on a newline above the line they are annotating.
* Put an empty line before the comment.

```
// Holds all the lines in the file.
var lines: Array<string>;

function walkFor(name: string, millis: number) {
    console.log(name + ' is now walking.');

    // Wait for millis milliseconds to stop walking
    setTimeout(() => {
        console.log(name + ' has stopped walking.');
    }, millis);
}
```

### Todo and XXX
`TODO` and `XXX` annotations help you quickly find things that need to be fixed/implemented.
* Use `// TODO:` to annotate solutions that need to be implemented.
* Use `// XXX:` to annotate problems the need to be fixed.
* It is best to write code that doesn't need `TODO` and `XXX` annotations, but sometimes it is unavoidable.

## Variable Declarations
* All variables must be declared prior to using them. This aids in code readability and helps prevent undeclared variables from being hoisted onto the global scope.
* Implied global variables should never be used.
* Declare each variable on a newline.

## Function Declarations
* There should be no space between the name of the function and the left parenthesis `(` of its parameter list.
* There should be one space between the right parenthesis `)` and the left curly `{` brace that begins the statement body.
* The body of the function should be indented according to filetype.
* The right curly brace `}` should be on a new line.
* The right curly brace `}` should be aligned with the line containing the left curly brace `{` that begins the function statement.

```
// Standard Function Syntax
accessor type function foo(type param1, type param2) {
    return 'foo';
}
```

## Names
* All variable and function names should be formed with alphanumeric `A-Z, a-z, 0-9` and underscore `_` charcters.
* All constants should use UPPER_SNAKE_CASE.
* All variable, module, and function names should use lowerCamelCase or UpperCamelCase (PascalCase) depending on filetype.

### Classes
* Classes/Constructors should use UpperCamelCase (PascalCase).
* Class properties names should use UpperCamelCase (PascalCase).
* `Private` and `private static` members in classes should be denoted with the `private` keyword.
* `Private`, `private static`, ansd `Protected` members should be prefaced with one underscore `_`.

* All class memebers should be listed at the top of the class defintion group be accessor.
* The constuctor(s) should be after the class members.
* The public functions should be listed after the constructor(s).
* `Private` functions should be group together at the end of the file.
* `Private` functions should be group together at the end of the file.
* In large files with many functions, it is recommend to place a divider comment between groups of functions


### Interfaces
* Interfaces should use UpperCamelCase.
* Interfaces should be prefaced with the capital letter I.
* Only `public` members should be in an interface, leave out `protected` and `private` members.


## Statements
### Simple
* Each line should contain at most one statement.
* A semicolon should be placed at the end of every simple statement.

### Compound
_Compound statements are statements containing lists of statements enclosed in curly braces `{}`._
* The enclosed statements should start on a newline.
* The enclosed statements should be indented according to filetype.
* The left curly brace `{` should be at the end of the line that begins the compound statement.
* The right curly brace `}` should begin a line and be indented to align with the line containing the left curly brace `{`.
* **Braces `{}` must be used around all compound statements** even if they are only single-line statements.
  _If you do not add braces `{}` around compound statements, it makes it very easy to accidentally introduce bugs._
* Compount statements do not need to end in a semicolon `;` with the exception of a `do { } while();` statement.

### Return
* If a `return` statement has a value you should not use parenthesis `()` around the value.
* The return value expression must start on the same line as the `return` keyword.
* It is recommended to take a return-first approach whenever possible.

### If
* Alway be explicit in your `if` statement conditions.
* Sometimes simply checking falsy/truthy values is fine, but the general approach is to be explicit with what you are looking for. This can prevent a lot of unnecessary bugs.

_If statements should take one of the following forms:_
```
if (/* condition */ ) { /* simple statement */; }

if (/* condition */ ) { /* simple statement */; }
else                  { /* simple statement */; }

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

```
for (/* initialization */; /* condition */; /* update */) {
    // ...
}
```

### While
_While statements should have the following form:_

```
while (/* condition */) {
    // ...
}
```

### Do While
* Do while statements should be avoided unless absolutely necessary to maintain consistency.
* Do while statements must end with a semicolon `;`

Do while statements should have to following form:
```
do {
    // ...
} while (/* condition */);
```

### Switch
* Each switch group except default should end with `break`, `return`, or `throw`.

_Switch statements should have one of the following forms:_
```
// Single Statement in Each Case
switch (/* expression */) {
    case /* expression */: /*Simple Statement*/;  /* termination */;
    case /* expression */: /*Simple Statement*/;  /* termination */;
    case /* expression */: /*Simple Statement*/;  /* termination */;
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

```
try {
    // ...
} catch (error) {
    // ...
}

try {
    // ...
} catch (error) {
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

```
if (condition) {
    // ...
}
```

* All operators except for period `.`, left parenthesis `(`, and left bracket `[` should be separated from their operands by a space.

```
var sum = a + b;
var name = person.name;
var item = items[4];
```

* No space should separate a unary/incremental operator `!x, -x, +x, ~x, ++x, --x, x++, x--` and its operand.

```typescript
var neg = -a;
```

* Each semicolon `;` in the control part of a `for` statement should be followed with a space.

```typescript
for(var i = 0; i < 10; ++i) {
    // ...
}
```




