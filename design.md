# Klyn Design Document

## Introduction

### What is Klyn?

Klyn is a programming language that is designed to be simple, expressive, and powerful. It is, principally, a functional
language that is designed to be easy to learn and use. It is designed to be a general-purpose language. It will be 
implemented in Kotlin using ANTLR, and will run on the JVM.

### Why Klyn?

Klyn is a learning project, to learn how efficiently and effectively a programming language can be 
designed and implemented.

### Inspiration

- Lisp (and derivatives)
- Lua
- Ruby
- Haskell
- Scala
- Elixir
- Kotlin

In that order.

### Philosophy

- Simplicity
- Minimalism
- Expressiveness

## Features

- Functional
- Object-oriented (Lua-style)
- Dynamic typing
- VM-based
- Garbage-collected
- REPL (in the future)
- Macros (in the future)
- JVM interop

## Syntax

### Types

- `JavaObject` - A Java object
- `KlynObject` - A Klyn object
- `Number` - A number (64-bit floating point)
- `Boolean` - A boolean
- `Atom` - A symbol
- `List` - A list
- `String` - A string
- `Function` - A function
- `Nil` - An empty object

### Examples

```
// This is a comment

// This is a number
let myNum = 1;

// This also a number
let pi = 3.14159;

// Booleans are the same as in other languages
let isTrue = true;
let isOne = (myNum == 1);

// Atoms are unique in the program
let myAtom = :myAtom;

// Lists are linked lists
let myList = [1, 2, 3, 4, 5];
let alsoList = ["foo", 1, true, :mix];

// Strings are immutable
let myString = "Hello, world!";
let alsoString = "This is" + " a string";

// Functions are first-class
let myFunc = (x) => x + 1;
let alsoFunc = (x) => {
    x + 1;
};

myFunc(1); // 2

// Nil is the empty object
let notDefinedYet; // nil
```

#### Control Flow

```
if (true) {
    // Do something
} else {
    // Do something else
}

let x = 1;
loop (x < 10) {
    x = x + 1;
}

let y = 1;
do {
    y = y + 1;
} loop (y < 10);

let arr = [1, 2, 3, 4, 5];
loop (let element in arr) {
    // Do something with element
}

loop (let i = 0; i < 10; i = i + 1) {
    // Do something
}
```

#### Blocks and blocks in blocks

```
let x = 1;
{
    let y = 2;
    x = x + y;
}

// y is not defined here
```

```
{
    let x = 2;
    {
        let x = 3;
    }
    // x is 2
}
// x is not defined here
```

```
let myStruct = {
    let inner = {
        let x;
        let y;
    };
    
    let z;
}

myStruct.inner.x = 1;
myStruct.inner.y = 2;
myStruct.z = 3;
```

#### has and is

```
// Take `myStruct` from the previous example

if (myStruct has inner) {
    // Do something, this is true
}

let copyStruct = myStruct;
if (copyStruct is myStruct) {
    // Do something, this is true
}
```

#### Functions

```
let add = (x, y) => x + y;
let addOne = (x) => add(x, 1);

add(1, 2); // 3

let double = (x) {
    x * 2;
}

// Pipe operator
let myValue = 2 |> double |> addOne; // 5

fn myFunc(x, y) { // Same as `let myFunc = (x, y) => x + y;`
    x + y;
}
```

#### Objects

```
// Everything is an object, that includes blocks and statements

let myObject = {
    let x = 1;
    let y = 2;
    
    let add = () {
        x + y;
    }
}

myObject.add(); // 3
```

## Roadmap

- v0.1 - CALM or C And Lisp Mixture, the first version of the language
  - Lexer
  - Parser
  - Interpreter
  - Basic types
  - Basic control flow
  - Basic functions
  - Only a simple C and Lisp mixture
- v0.2 - JVM interop
- v0.3 - Macros
- v0.4 - REPL
- v0.5 - v0.9 - More features, undefined exactly what
- v1.0 - First stable release

## License

All code or anything related to Klyn is licensed under the Apache 2.0 License. 
See the `LICENSE` file for more information.
```