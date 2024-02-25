---
title: "JavaScript Execution Context - How does JS work on behind?"
datePublished: Sun Feb 25 2024 02:35:27 GMT+0000 (Coordinated Universal Time)
cuid: clt0wduek000509jt9h8c89pg
slug: javascript-execution-context-how-does-js-work-on-behind
tags: javascript, web-development, javascript-library, frontend-development

---

Welcome back to my blogs. Let's delve deeper into the JavaScript execution context with more detailed explanations and examples.

JavaScript execution context is a fundamental concept that plays a crucial role in how JavaScript code is executed. It involves the creation and management of environments where code runs. This article will explore the different types of execution contexts, their characteristics, and how they contribute to the overall behaviour of JavaScript programs.

## Global Execution Context

The global execution context is the default context in which JavaScript code runs. It represents the entire script and contains globally declared variables and functions. Variables declared with `let`, `const`, or `var` outside of any function or block scope become properties of the global object (`window` in browsers).

```javascript
let globalVar = 'I am global'; // Global variable

function globalFunction() {
  console.log('Global function called');
}

console.log(globalVar);         // Output: 'I am global'
globalFunction();               // Output: 'Global function called'
```

In the example above, `globalVar` and `globalFunction` are part of the global execution context. The `console.log` statements access and display the global variable and call the global function.

## Function Execution Context

Function execution contexts are created when functions are invoked. Each function call generates its execution context, encapsulating local variables, parameters, and a reference to the outer (enclosing) execution context, forming what is known as the scope chain.

```javascript
function outerFunction(outerParam) {
  let outerVar = 'I am outer';

  function innerFunction(innerParam) {
    let innerVar = 'I am inner';
    console.log(outerParam);    // Accessing parameter from the outer function
    console.log(outerVar);      // Accessing variable from the outer function
    console.log(innerParam);    // Accessing parameter from the inner function
    console.log(innerVar);      // Accessing local variable
  }

  innerFunction('Inner Param');
}

outerFunction('Outer Param');
```

In this example, `outerFunction` is called with the parameter `'Outer Param'`. Inside `outerFunction`, `innerFunction` is called with the parameter `'Inner Param'`. The inner function has access to both its local variables and the variables/parameters of the outer function due to the scope chain.

## Scope and Scope Chain

Scope refers to the region of code where a particular variable can be accessed or modified. JavaScript uses lexical scoping, which means the scope is determined by the placement of variables and functions in the source code.

The scope chain is a hierarchical structure that defines the order in which JavaScript looks for variables. When a variable is accessed, JavaScript first looks in the current scope. If the variable is not found, it looks in the next outer scope, continuing up the chain until the global scope.

```javascript
function outerScope() {
  let outerVar = 'I am in the outer scope';

  function innerScope() {
    let innerVar = 'I am in the inner scope';
    console.log(outerVar);  // Accessing variable from the outer scope
  }

  innerScope();
}

outerScope();
```

In this example, `innerScope` has access to `outerVar` because of the scope chain. When `console.log(outerVar)` is executed inside `innerScope`, JavaScript looks in the inner scope first, doesn't find `outerVar`, then looks in the outer scope where it finds and logs the variable.

## Closures

Closures are a powerful concept in JavaScript that arises from the combination of functions and the scope chain. A closure occurs when a function is defined inside another function, and the inner function has access to the outer function's variables, even after the outer function has finished executing.

```javascript
function outerClosure() {
  let outerVar = 'I am from the closure';

  function innerClosure() {
    console.log(outerVar);  // Accessing variable from the outer function
  }

  return innerClosure;
}

const closureFunction = outerClosure();
closureFunction();  // Output: 'I am from the closure'
```

In this example, `outerClosure` returns `innerClosure`, forming a closure. When `closureFunction` is invoked, it still has access to the `outerVar` variable from the outer function, even though `outerClosure` has completed its execution.

## The Execution Stack (Call Stack)

The execution stack, often referred to as the call stack, is a mechanism that manages the order of execution contexts in JavaScript. When a function is called, a new execution context is pushed onto the stack. When the function completes, its context is popped off the stack.

The call stack is a crucial component in understanding the flow of code execution. It is a data structure that follows the Last In, First Out (LIFO) principle, meaning the last function called is the first to be executed. The call stack keeps track of the currently executing context.

### How the Call Stack Works

1. **Function Invocation:**
    
    * When a function is called, a new execution context is created.
        
    * The context is pushed onto the call stack.
        
2. **Execution:**
    
    * The JavaScript engine executes the statements within the current context.
        
3. **Return:**
    
    * Once the function completes execution, its context is popped from the call stack.
        

### Recursion and the Call Stack

Recursion, a technique where a function calls itself, demonstrates the recursive nature of the call stack. Each recursive call adds a new context to the stack until the base case is reached, at which point the stack starts unwinding.

## Example: Understanding Execution Context and Call Stack

Let's explore a simple example to illustrate these concepts:

```javascript
function greet(name) {
    let message = `Hello, ${name}!`;
    console.log(message);
}

function welcome() {
    let greeting = 'Welcome to JavaScript!';
    greet('User');
    console.log(greeting);
}

welcome();
```

1. **Global Execution Context:**
    
    * Created initially.
        
    * Variables like `greet` and `welcome` are added to the global scope.
        
2. **Execution of**`welcome` Function:
    
    * `welcome` function is called, creating a new execution context.
        
    * `greeting` variable is added to the `welcome` context.
        
    * `greet` function is called, creating another execution context.
        
    * `message` variable is added to the `greet` context.
        
    * Log statements execute in the reverse order.
        
3. **Call Stack Visualization:**
    

* ```javascript
      |   greet()   |  <- greet context
      |  welcome()  |  <- welcome context
      |  (global)   |  <- global context
    ```
    
    * The call stack is visualized with the current execution context at the top.
        
    
* **Call Stack Unwinding:**
    
    * As functions complete execution, their contexts are popped from the stack.
        

1. ```javascript
     |  (global)   |  <- global context
    ```
    
    * The call stack is empty once all functions complete execution.
        
    

## Asynchronous JavaScript and the Event Loop

JavaScript is often involved in asynchronous operations, such as handling user input or making API requests. To manage these scenarios, JavaScript employs the event loop and callback queue.

### Event Loop

The event loop is a continuous process that checks the call stack and the callback queue. If the call stack is empty, the event loop dequeues functions from the callback queue and adds them to the call stack for execution.

### Callback Queue

When an asynchronous operation completes, a callback function is pushed into the callback queue. The event loop ensures that these callbacks are executed in the correct order.

## Debugging Execution Context and Call Stack

Understanding how to debug issues related to execution context and the call stack is essential for efficient JavaScript development. Modern browsers provide robust developer tools that enable developers to inspect and debug code execution.

1. **Browser Developer Tools:**
    
    * Utilize the "Sources" panel to set breakpoints, inspect variables, and step through code.
        
    * The call stack and current execution context are visible in the "Call Stack" and "Scope" panels.
        
2. **Console Logging:**
    
    * Insert `console.log` statements strategically to log variable values and track the flow of execution.
        
3. **Debugger Statement:**
    
    * Place the `debugger` statement in the code to pause execution and open the debugger when reached.
        

```javascript
function example() {
    debugger;
    // Code to be inspected
}
```

## The `this` Keyword

The `this` keyword refers to the object to which a function belongs or the object that is the current execution context. Its value is determined by how a function is called, and it can behave differently in various situations.

```javascript
const myObject = {
  property: 'I am a property',
  method: function() {
    console.log(this.property);  // Accessing property using 'this'
  }
};

myObject.method();  // Output: 'I am a property'
```

In this example, `this` within the `method` function refers to the `myObject` because it is the object that the function is a method of. Understanding the context in which `this` is used is crucial for effective object-oriented programming in JavaScript.

## Dynamic Nature of Execution Context

JavaScript is a dynamically typed and loosely-typed language, meaning that variables can change their types, and the type of a variable is determined at runtime. This dynamic nature extends to execution contexts as well.

```javascript
function dynamicContextExample() {
  if (true) {
    var dynamicVar = 'I am dynamically scoped';
  }

  console.log(dynamicVar);  // Output: 'I am dynamically scoped'
}

dynamicContextExample();
```

In this example, `dynamicVar` is declared using `var` inside a block. However, due to the lack of block-scoping with `var`, `dynamicVar` is accessible outside the block. Understanding the dynamic nature of execution contexts helps in avoiding unexpected behaviour in your code.

## Call Stack

The call stack is a crucial component in understanding the flow of code execution. It is a data structure that follows the Last In, First Out (LIFO) principle, meaning the last function called is the first to be executed. The call stack keeps track of the currently executing context.

### How the Call Stack Works

1. **Function Invocation:**
    
    * When a function is called, a new execution context is created.
        
    * The context is pushed onto the call stack.
        
2. **Execution:**
    
    * The JavaScript engine executes the statements within the current context.
        
3. **Return:**
    
    * Once the function completes execution, its context is popped from the call stack.
        

### Recursion and the Call Stack

Recursion, a technique where a function calls itself, demonstrates the recursive nature of the call stack. Each recursive call adds a new context to the stack until the base case is reached, at which point the stack starts unwinding.

## Example: Understanding Execution Context and Call Stack

Let's explore a simple example to illustrate these concepts:

```javascript
function greet(name) {
    let message = `Hello, ${name}!`;
    console.log(message);
}

function welcome() {
    let greeting = 'Welcome to JavaScript!';
    greet('User');
    console.log(greeting);
}

welcome();
```

1. **Global Execution Context:**
    
    * Created initially.
        
    * Variables like `greet` and `welcome` are added to the global scope.
        
2. **Execution of**`welcome` Function:
    
    * `welcome` function is called, creating a new execution context.
        
    * `greeting` variable is added to the `welcome` context.
        
    * `greet` function is called, creating another execution context.
        
    * `message` variable is added to the `greet` context.
        
    * Log statements execute in the reverse order.
        
3. **Call Stack Visualization:**
    

* ```css
        |   greet()   |  <- greet context
        |  welcome()  |  <- welcome context
        |  (global)   |  <- global context
    ```
    
    * The call stack is visualized with the current execution context at the top.
        
    
* **Call Stack Unwinding:**
    
    * As functions complete execution, their contexts are popped from the stack.
        

1. ```basic
      |  (global)   |  <- global context
    ```
    
    * The call stack is empty once all functions complete execution.
        
    

## Asynchronous JavaScript and the Event Loop

JavaScript is often involved in asynchronous operations, such as handling user input or making API requests. To manage these scenarios, JavaScript employs the event loop and callback queue.

### Event Loop

The event loop is a continuous process that checks the call stack and the callback queue. If the call stack is empty, the event loop dequeues functions from the callback queue and adds them to the call stack for execution.

### Callback Queue

When an asynchronous operation completes, a callback function is pushed into the callback queue. The event loop ensures that these callbacks are executed in the correct order.

## Debugging Execution Context and Call Stack

Understanding how to debug issues related to execution context and the call stack is essential for efficient JavaScript development. Modern browsers provide robust developer tools that enable developers to inspect and debug code execution.

1. **Browser Developer Tools:**
    
    * Utilize the "Sources" panel to set breakpoints, inspect variables, and step through code.
        
    * The call stack and current execution context are visible in the "Call Stack" and "Scope" panels.
        
2. **Console Logging:**
    
    * Insert `console.log` statements strategically to log variable values and track the flow of execution.
        
3. **Debugger Statement:**
    
    * Place the `debugger` statement in the code to pause execution and open the debugger when reached.
        

```javascript
function example() {
    debugger;
    // Code to be inspected
}
```

## Conclusion

Understanding JavaScript execution context and the call stack is fundamental for writing efficient and bug-free code. Developers benefit from grasping how functions are invoked, how the call stack operates, and how asynchronous operations are managed through the event loop.