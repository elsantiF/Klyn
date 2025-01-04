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

- Lisp (and derivatives, specially Clojure)
- Lua
- Ruby
- Haskell
- Scala
- Elixir
- Kotlin
- Groovy

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
- `Boolean` - A boolean
- `Atom` - A symbol
- `List` - A list
- `Char` - A character (16-bit)
- `String` - A string
- `Function` - A function
- `Nil` - An empty object

Numeric types:

- `Byte` - An 8-bit integer
- `UByte` - An unsigned 8-bit integer
- `Short` - A 16-bit integer
- `UShort` - An unsigned 16-bit integer
- `Int` - A 32-bit integer
- `UInt` - An unsigned 32-bit integer
- `Long` - A 64-bit integer
- `ULong` - An unsigned 64-bit integer
- `Float` - A 32-bit float
- `Double` - A 64-bit float

Additionally, there are extra types:

- `Block` - A block of code
- `Array` - An array
- `Map` - A map
- `Set` - A set

### Examples

```
// This is a comment

// This is a integer, by default it is a 32-bit integer
let myNum = 1;

// This is a float, by default it is a 32-bit float
let pi = 3.14159;

// Booleans are the same as in other languages
let isTrue = true;
let isOne = (myNum == 1);

// Atoms are unique in the program
let myAtom = :myAtom;

// Lists are linked lists
// They can contain any type of object, they are mutable
let myList = [1, 2, 3, 4, 5];
let alsoList = ["foo", 1, true, :mix];

// Strings are mutable
let myString = "Hello, world!";
let alsoString = "This is" + " a string";

// Functions are first-class
let myFunc = (x) -> x + 1;
let alsoFunc = (x) -> {
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

// `loop` keyword is the only way to do loops
// can be used as a traditional while loop
let x = 1;
loop (x < 10) {
    x = x + 1;
}

// as a do-while loop, with the keyword `do`
let y = 1;
do {
    y = y + 1;
} loop (y < 10);

// as a traditional for loop
loop (let i = 0; i < 10; i = i + 1) {
    // Do something
}

// as a for loop in modern languages
let arr = [1, 2, 3, 4, 5];
loop (let element in arr) {
    // Do something with element
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

// `has` checks if a property exists in a object
if (myStruct has inner) {
    // Do something, this is true
}

// `is` checks if a object is of a certain type
let copyStruct = myStruct;
if (copyStruct is myStruct) {
    // Do something, this is true
}
```

### Casting

```
let myNum = 1;
let myFloat = myNum as Float;
```

#### Functions

```
let add = (x, y) -> x + y;
let addOne = (x) -> add(x, 1);

add(1, 2); // 3

let double = (x) {
    x * 2;
}

// Pipe operator
let myValue = 2 |> double |> addOne; // 5

fn myFunc(x, y) { // Same as `let myFunc = (x, y) -> x + y;`
    x + y;
}
```

#### Objects

```
// Everything is an object, that includes blocks of code

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
