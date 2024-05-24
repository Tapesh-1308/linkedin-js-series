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

# JavaScript: Types of Errors 🤡

Three types of errors you can see in JavaScript:

## Reference Errors

When you attempt to use a variable (or a reference) that has not been declared.

- Accessing undeclared variables.
- Accessing a variable outside of its scope.

## Syntax Errors (no line executes in this case)

When code does not conform to the structure or syntax rules of the JavaScript language.

- Incorrect use of language constructs.
- Missed or extra punctuations.

## Type Errors

When an operation is performed on a value of an unexpected type.

- Trying to call a function that is not a function.
- Accessing properties or methods of `null` and `undefined`.

## Can You Answer This Question? 👇

Which type of error will this snippet give?

```javascript
function testFunction() {
  console.log(answer);
}

testFunction();
```

# JavaScript: Block Scope & Shadowing🔥

## Topics Covered
- Block
- Block Scope
- Shadowing
- Illegal Shadowing

## What is a Block? (compound statement)
A block is defined by curly braces `{...}`.
- Used to combine multiple JavaScript statements into one group.
- We can use it where JavaScript expects one single statement.

**Example:**
```javascript
if (true) {
  // block
}
```

## Block Scoped
- Scope in which we can access all variables and functions of that block. Lexical scope also works here.

**Note:**
- `let` and `const` are block scoped, meaning they cannot be accessed outside the block.
- `var` is globally scoped.

## Shadowing
- If we have the same named variable outside the block, then the block variable shadows the outside variable.

**Example:**
```javascript
let a = 1; // shadowed
{
  let a = 2;
  console.log(a); // 2
}
```

Because `let` and `const` variables are stored in different memory locations: in the block object for block variables, and in the script object for global variables.

**In short:**
- Global: reserved for `var`
- Script: for `let` and `const` (outside block)
- Block: separate memory for variables (`let` and `const`) inside scope

## Illegal Shadowing
- When an outside variable is declared with `let` or `const`, but inside the block, it is declared with `var`.
- If a variable is shadowing any outside variable, it should not cross the boundary of its scope.

**Example:**
```javascript
let a = 10;
{
  var a = 20; // illegal shadowing
}
```

However:
```javascript
var a = 10;
{
  let a = 20; // works fine since let creates a separate block
}
```

# JavaScript: Closures 🔥

A closure is the combination of a function bundled together with a reference to its lexical environment. 

In JavaScript, a closure is a function that remembers its outer variables and can access them even when called independently. 

## Advantages
- Data handling / encapsulation
- State retention
- Currying (will study later) 
- Memoization
- Asynchronous programming
- Event handling

## Disadvantages
- Variables declared inside a closure are not garbage collected. 
- Garbage collection is done when function execution gets completed. All the variables are deleted from memory.
- Too many closures can slow down your application, caused by duplication of code in memory.

# JavaScript: Callback Functions 🔥

## Callback Functions

In JavaScript, callback functions are functions passed as arguments to another function, enabling asynchronous behavior.

### Need of Callback Functions

- **Asynchronous JavaScript**: Callback functions aid in the development of asynchronous JavaScript code.
- **Execution Control**: Ensures that a function does not execute until a specific task is completed, but rather runs immediately after task completion.

### Usage

1. **Event Handling**: Callback functions are commonly used for event handling.
2. **Web APIs**: Utilized with functions such as `setTimeout` or `setInterval`.
3. **Data Fetching**: In scenarios like fetching data from external sources.

See the image below for visual representation:


### Tips

- **Event Listener Optimization**: Removing event listeners when not in use can optimize memory usage, preventing potential slowdowns on websites.

# JavaScript: Working of Async Code 🔥

## Prerequisite: Callback Function

### Blocking 🔥

- When tasks that take a lot of time (e.g., API calls, image processing) are executed in the main thread, they block the call stack or main thread until completion.
- **Issue**: Blocking the main thread can lead to performance issues.

**Solution**: Async Callbacks

### Process of Execution 🔥

1. All callbacks are registered in the Web API with their attached timer and event.
2. Meanwhile, other code continues to execute.
3. When the timer expires or the callback is ready, it is pushed to the task queue but is not executed immediately.

### Event Loop 🔁

- The event loop checks if the call stack is empty.
  - If empty, it looks into the microtask queue and task queue for pending callbacks.
  - If a pending callback exists, the event loop pushes it to the top of the call stack for execution.

### Microtask Queue 🔥

- Introduced in ES6.
- Used for promises and MutationObserver (changes in the DOM tree).
- Has higher priority than the task queue.
  - The task queue must wait until the microtask queue is empty.

### Starvation of Task Queue 🍴

- Occurs when resolved promises keep adding to the microtask queue, preventing the task queue callbacks from executing.
- This can delay task queue callbacks indefinitely.

### Note

During Event Listener usage, the original callback remains in the Web API environment indefinitely because the event may occur again. Therefore, it is recommended to remove listeners when not in use to allow the garbage collector to free up memory.

### FAQs

**Q. When does the Event Loop actually start?**

**A.** The event loop is always running and doing its job.

**Q. Are only async callbacks registered in the Web API?**

**A.** Yes, only async code moves to the Web API.

**Q. Does the Web API store only callback functions and push the same to the queue?**

**A.** Yes, callback functions are stored and a reference is scheduled in queues.

**Q. What if `setTimeout` delay is 0 ms?**

**A.** Even with a 0 ms delay, the callback goes through the whole process and waits for the call stack to be empty.

# How JavaScript Engine Works 🚂💨

A browser has two main components:
- **JavaScript Engine**
- **Rendering Engine**

### JavaScript Engine

The JavaScript Engine executes and compiles JavaScript into native machine code.

- **Chrome**: v8 🔻
- **Firefox**: SpiderMonkey 🐒
- **Safari**: JavaScriptCore 💥
- **Edge (IE)**: Chakra ✳️

### Rendering Engine

The Rendering Engine is responsible for rendering DOM trees, styles, events, etc. It paints the content on your screen.

### JS Engine Architecture

- **Not a machine**: It's a program written in a low-level language.
- **Function**: Takes high-level code (JavaScript) and converts it into machine-level code.

#### Three MAIN steps to execute the code:

1. **Parsing**
2. **Compilation**
3. **Execution**

### 1. Parsing

- **Process**: Reads code line by line.
- **Steps**:
  1. Breaks down code into tokens.
  2. Passes tokens to a syntax parser.

**Syntax Parser**: Converts the code into an AST (Abstract Syntax Tree).

**AST**: Represents code as a tree-like structure.

### 2. Compilation

JavaScript uses JIT (Just-In-Time) compilation, involving both an interpreter and a compiler.

- **Process**:
  1. AST goes to the interpreter (converted to high-level code).
  2. Byte code then goes for execution.

During step 1, the compiler helps optimize the code at runtime.

### 3. Execution

Execution is not possible without the memory heap and call stack.

- **Memory Heap**: Where all variables and functions are assigned to memory. It also includes a garbage collector to free up memory space whenever possible.

**Garbage Collector**: Uses the mark-and-sweep algorithm to free up memory. 🚮

### Note

All browsers work differently, but the above steps are used by v8 and most engines work similarly.

# JavaScript: Callbacks Problems 🔥

### Mainly two problems with callbacks:

1. **Callback Hell**
2. **Inversion of Control**

### 1. Callback Hell ☠️

Callback hell occurs when multiple callbacks are nested within a function.

- The shape of the code resembles a pyramid ("pyramid of doom").
- This makes the code difficult to maintain and understand.

### 2. Inversion of Control 🤸🏻‍♂️

Inversion of control means losing control over the code when using callbacks. 

- Control is given to another nested callback function, increasing dependency.
- Essentially, we don't know what's happening behind the scenes.

### SOLUTION??

**Promises** 🔥

# JavaScript: Promises 🔥

A Promise is an assurance or guarantee that something will happen in the future.

It can have two outcomes:
- Fulfillment
- Failure

In JavaScript,
a Promise is an object that will produce a single value after some time in the future.

**Value:**
- If successful: resolved value
- If failed: reason

Promises can have 3 possible states:
- Pending: default state
- Fulfilled: if successful
- Rejected: if failed

Promise transitions from:
- pending -> fulfilled OR
- pending -> rejected

When using Promises, we have full control over the logic, allowing us to solve the inversion of control problem using promises.

### How to create promises?

- Using `.then()` method:
  - It takes two callbacks:
    1. If resolved
    2. If rejected
  - `.then((value) => {}, (reason) => {})`

- Always returns another promise, facilitating easy chaining.
- Chaining helps solve the callback hell problem.

### How to handle errors in promises?

- Using `.catch()` method:
  - If anything goes wrong in the promise, this method catches the reason for the error.
  - Using catch, errors no longer remain uncaught.

### `.finally()`

- Method that always runs, regardless of whether resolved or rejected.
- Here we can handle the result of promises whether rejected or resolved.

# JavaScript: Promise APIs 🔥🔥

Promises in JavaScript are used to handle asynchronous operations. There are several Promise APIs that allow you to work with multiple promises efficiently.

## Promise APIs

### 1. `Promise.all()`

- Used to run multiple promises in parallel.
- Takes an iterable (array) of promises as an argument.
- If all promises are fulfilled, returns an array of values after resolving.
- If any promise is rejected, stops running and returns the error immediately.
- Implements fail-fast behavior.

### 2. `Promise.allSettled()`

- Introduced after ES2020.
- Returns an array of all settled promises, whether fulfilled or failed.
- Each array value is an object with properties:
  - `status`: Indicates whether the promise was fulfilled or rejected.
  - `value` or `reason`: Contains the resolved value or rejection reason, respectively.

### 3. `Promise.race()`

- Returns a single promise as output.
- Returns the promise that settles first (either fulfilled or rejected).
- If the fastest promise is resolved, it stops there, and other promises are not executed.
- If the fastest promise is rejected, it will not get any error if other promises failed or not because they will not get executed.

### 4. `Promise.any()`

- Returns a single promise that resolves when any of the provided promises resolves.
- If no promise is fulfilled, returns an *aggregate error*.
- *Aggregate Error*: Represents several errors wrapped in a single error. It provides the reasons for rejection of all promises in an array.

## Conclusion

These Promise APIs provide powerful tools for handling asynchronous operations and managing multiple promises effectively.

Next Topic: Async/Await 🔥

# JavaScript: Async/Await 🔥

Async/Await is syntactical sugar over `.then()` and `.catch()` chains, making promises handling more elegant.

## Async

- Keyword to create an asynchronous function.
- This function always returns a promise. If we don't explicitly return a promise, JavaScript automatically wraps the returned value in a promise.

## Await

- Keyword that makes JavaScript wait until the promise is resolved or rejected.
- Whenever the JavaScript engine encounters the `await` keyword, it suspends the complete function call from the call stack and continues with other work.
- Once the promise is settled, the function comes back in the call stack and continues executing.
 
`As time, tide, and JavaScript wait for none 😉`

### Why Async/Await?

- No need for nested callbacks.
- Simplified syntax.
- No chaining required.

## Error Handling

- Use `try/catch` for error handling with Async/Await.

```javascript
try {
  // Try to resolve promise here
} catch (error) {
  // Do work when an error occurs
} finally {
  // Run regardless of whether the promise is resolved or rejected
}
```
# JavaScript: `this` keyword 🔥

- `this` always refers to an object.
- The object it refers to will vary depending on how and where `this` is being called.
- It's not a variable, but a keyword (its value is not changed or reassigned).

## `this` in Global Scope

- Refers to the global object:
  - `window` in the browser
  - `global` in Node.js

## `this` inside Functions

- The value depends on strict/non-strict mode (will discuss in the next post):
  - In strict mode: `this` refers to `undefined`.
  - In non-strict mode: `this` refers to the global object. Why?
    - It also depends on how it is being called:
      - `function () {}`: `this` is `undefined`.
      - `window.function() {}`: `this` is `window` because it got a reference to the window.

- This substitution:
  - If `this` is `undefined` or `null`, the `this` keyword will be replaced with the global object in non-strict mode.

## `this` inside an Object Method

- Refers to the object.

## `this` inside Arrow Functions

- Arrow functions do not have their own `this`.
- They take `this` from their enclosing lexical environment.

## `this` inside DOM

- Refers to the element where called:
  ```html
  <button onclick="console.log(this)"></button>
  ```
- Prints the button element.

## `this` in call(), apply(), bind()
 - Will see later.

# JavaScript: "use strict" 🔥

"use strict" was introduced in ES5 and it makes JavaScript code execute in strict mode. It can be declared at the beginning of a script or a function.

## WHY?

- **Easier to Write Secure JavaScript**: It helps catch common coding errors and unsafe actions, making code more robust.
- **Throws Errors for Bad Syntax**: It throws errors for practices that are not considered good or safe.

## WHAT WE CAN'T DO?

- Using variables/objects without declaring them using `var`, `let`, or `const`.
- Deleting variables and function names.
- Having duplicate parameters in a function.
- Using octal numeric literals.
- Writing to read-only properties.
- Deleting undeletable properties.
- Using certain keywords (`eval`, `arguments`, `private`, `public`, `static`, etc.) as variable names.
- Declaring variables using the `eval` function.
- This behaves differently inside functions.

# JavaScript: call(), apply(), bind() 🔥

## call()

- **Purpose**: Change the context of the invoking function, allowing the replacement of the value of 'this' inside a function with any desired value.
- **Syntax**: `func.call(newThisObj, arg1, arg2, ...)`
  - `newThisObj`: Value to replace 'this' inside the function. If not provided, the global object is considered.
  - `args`: Other required arguments for the function, if any.

## apply()

- **Purpose**: Similar to `call()`, but arguments are passed as an array.
- **Syntax**: `func.apply(newThisObj, [arg1, arg2, ...])`

## bind()

- **Purpose**: Creates a copy of a function with a new value of 'this', which can be invoked later.
- **Syntax**: `newFunc = func.bind(newThisObj, arg1, arg2, ...)`
  - `newFunc`: New function with the specified 'this' context.
  - `newThisObj`: Value to replace 'this' inside the function.
  - `args`: Other required arguments for the function.

# JavaScript: Currying 🍛 🔥

Transforms a function with multiple arguments into a nested series of functions, each taking a single argument.

f(a, b, c) -> f(a)(b)(c) ☠️

## Why Currying?

- helps avoid passing the same variable again and again
- helps to create Higher Order Functions
- fewer errors and side effects

[enables checking method: checks if you have all the required things before you proceed]

See the examples in the below image 🖼

## Currying vs Partial Application 🔥

- In currying, nested functions are equal to arguments, means each function must have a single argument.

f(a, b, c) -> f(a)(b)(c)

- Partial Application transforms a function into another function with smaller arguments (less args).

f(a, b, c) -> f(a)(b, c)

## Currying using bind()

- For currying, we can also use the bind function and separate the args in separate functions
- because bind returns a new function.

```javascript
curry = func.bind(this, arg1);
curry(arg2);
```
☠️ This topic needs a video reference to understand properly, so do youtube ▶️ to see more examples.
