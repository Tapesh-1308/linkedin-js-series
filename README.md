# JavaScript: Getting Started 🔥

## Introduction to ECMAScript

Before diving into JavaScript, let's get acquainted with ECMAScript, the standard on which JavaScript is based.

### Versions of ECMAScript

- **ES1** - 1997 (First release)
- ⭐ **ES6** - 2015 (Major changes introduced)
- **ES13** - 2022 (Latest version)

## What is JavaScript?

JavaScript is a versatile scripting language primarily used for web development. Here's a brief overview:

- **Purpose**: Used to add interactivity and dynamic effects to web pages.
- **File Extension**: `.js`
- **Usage**: Initially designed for client-side development, but now also used in server-side development.
- **Typing**: Dynamically typed (no need to specify data types).
- **Concurrency Model**: Asynchronous single-threaded language.

### Frameworks and Libraries

- **Frontend Frameworks**: React, Angular, Vue, etc.
- **Backend Frameworks**: Express, Node.js

## JavaScript Engine

To run JavaScript, we need a JavaScript engine that executes and compiles JS into native machine code. 

### Common JavaScript Engines

- **Chrome**: V8
- **Firefox**: SpiderMonkey
- **Safari**: JavaScriptCore
- **Edge (IE)**: Chakra

## Running JavaScript Outside the Browser

JavaScript can be executed outside the browser using Node.js.

### Node.js

Node.js is an open-source, cross-platform JavaScript runtime environment that executes JavaScript code outside of a web browser. It's commonly used for:

- Server-side applications
- Command-line tools
- Scalable network programs

---

This guide provides a brief introduction to JavaScript and its related technologies. For a deeper dive, consider exploring each topic in more detail.

# JavaScript: Data types and variables 🔥

Variables are like a container that store some data. 

In JavaScript we can declare variables in three ways that is using var, let, and const. 

General Rules for variable names: 
- cannot start with a number
- names are case sensitive
- names can only contains letters, digits and underscores _



## Data Types

In JavaScript we can classify data types in two types

1. Primitive Data Types [ simple ]
 - Numbers
 - Strings
 - Booleans
 - Null
 - Undefined
 - Big Int
 - Symbol

2. Objects: 
- Object stores data in key-value pairs 
- They are mutable (can be modified)
- Considered as complex Data structure
[ Example: Object, Array, Date Object ]


## 🔥 var vs let vs const 🔥

**var**
- introduced in early days
- limitations: it is function scoped not block scoped

Means - variables are accessible within entire function in which they are declared, rather than just within the block of code they appear


**let**
- introduced in es6
- block scoped
- value can be reassigned

**const**
- introduced in es6
- block scoped
- value can not be reassigned
- must assign value while declaration 

# JavaScript: Execution Context ⭐

When the JS engine scans code, it creates an environment called the Execution Context.

## Types of Execution Context

1. **Global EC**: Created when JS code first starts to run and represents the global scope in JS.
2. **Function EC**: Created when a function in the code starts executing.

## Execution Phases

### 1. Memory Creation Phase
- Allocates location to variables and functions.
- Stores variables with value as `undefined` and function references (i.e., the complete function definition).

### 2. Execution Phase
- Starts through the entire code line by line.
- Assigns values to variables in memory.
- For functions, when invoked, JS creates a new function EC.
- When a function returns a value, the function EC is destroyed.

*Once the entire code execution is done, the Global EC will be destroyed as well.*

## Call Stack (Last In First Out)

- To keep track of contexts, JS uses a call stack.
- A call stack has a fixed size depending on the system or browser.
- Exceeding the size limit causes a stack overflow error.

We will explore more about scopes and how the JS engine works internally in later posts. So stay tuned ✨

# JavaScript Hoisting - Explained EASILY

## Prerequisite
- JavaScript Execution Process
- Basic knowledge of Scope

Hoisting is a behavior in JavaScript where all declarations of a function, variable, or class go to the top of the scope they are defined in.

This whole process is done during the Memory Creation Phase. 
Let's see what actually happens with:

### Variables
- **`var`**: Variables are hoisted but with a default value of `undefined`.
- **`let` and `const`**: Hoisted but inaccessible before default initialization. [Gives Error when accessed before initialization]

### Functions
Functions become accessible even before the line they are declared. Hoisting does not occur in function expressions, it occurs only in function declarations.

### Point to Note
- Hoisting happens based on the scope. It sets variables and functions to the top of the scope.

### Related Topic: Temporal Dead Zone
- Area where variables are hoisted but inaccessible until they are initialized with a value. [Applies to `let` and `const`, not to `var`]


## From where I learned Hoisting?
- Watch this video: [Akshay Saini's video](https://lnkd.in/gfdGax5P) 🚀
- Read this freeCodeCamp Article: [freeCodeCamp Article](https://lnkd.in/gyP6Qc_s)

# JavaScript: Function Declaration vs Function Expression and Much More🔥

## Function Declaration (aka function statement) 👀

- Named function where you declare a name after the `function` keyword.

Example:
```javascript
function myFunc() {
  // function body
}
```

## Function Expression 👀

- Anonymous functions, where we use the `function` keyword without a name, then assign it to a variable.

Example:
```javascript
const myFunc = function () {
  // function body
};
```

* Here you can use `var` or `let` as well.
  - If `var` is used, it will store `undefined` in the memory creation phase.
  - If `let` and `const` are used, it will throw an error: we cannot access them before initialization.

### Function Expression (Benefits and Drawbacks)
- Cannot be accessed before initialization.
- Needs to be assigned to be used later.
- Anonymous functions are useful for anonymous operations, e.g., IIFEs, callback functions, etc.

We can also have named function expressions like this:

```javascript
const print = function x() {
  // function body
};
```
But here `x` is not accessible.

## Common Confusion: Parameters and Arguments

- **Parameters**: In function definition.
  ```javascript
  function myFunc(param1, param2) {
    // function body
  }
  ```

- **Arguments**: While calling functions.
  ```javascript
  let sum = add(arg1, arg2);
  ```

## First Class Functions / Citizens

- Ability to use functions like values.

In JavaScript, we can:
- Assign a function to a variable.
- Pass a function as an argument.
- Return a function from another function.

So, JavaScript functions are first class 🔥

# JavaScript: undefined vs Not defined🔥

## Undefined
- Predefined global variable that represents the value assigned to a variable during the memory creation phase.

## Not defined
- Means the variable has not been declared at all. Accessing such a variable results in a reference error.

## Sum up 💪
A variable that has been declared but not assigned a value is `undefined`, and a variable that has not been declared at all is `not defined`.

# JavaScript: Scope and Lexical Scope 🔥

## Disclaimer ⚠
This post is content-heavy.

## Scope
- Area where an item (variable or function) is visible and accessible to other code.

## Lexical Scope (Static Scope)
- A place where all the variables and functions of a parent lie. This scope is passed to the children scope (nested scope).

Consider this code and call stack:

```javascript
let name = "Tapesh";
function a() {
  function b() {
    function c() {
      console.log(name);
    }
    c();
  }
  b();
}
a();
```

### Call Stack
```
| C() |
| B() |
| A() |
| GEC |
|-----|
```

### Explanation

- `C()` has access to variables and functions in its own scope + lexical scope of its parent (`B()`).
- `B()` has access to its own scope + lexical scope of its parent (`A()`).
- `A()` has access to its own scope + lexical scope of its parent (Global Execution Context).
- Global Execution Context (GEC) has access to its own scope + parent (since it has no parent, it points to `null`).

## Scope Chain ⛓

- Determines the hierarchy where JS code must go through to find the lexical scope (origin) of a specific variable.

As in the above example:
- Code first finds the `name` variable in `C`'s scope.
- If not found, it goes to its lexical scope (that is `B`'s scope).
- If not found, it goes to `A`'s scope.
- If not found, it goes to GEC (found ✔).
- If not found, it returns a "not defined" error.

### Chain
C -> B -> A -> GEC