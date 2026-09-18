## What is the global execution context?

The global execution context is the default execution context created when JavaScript code starts running. It provides the global object and allows the code to execute in the global scope.

## Where is the task queue stored?

The task queue is managed by the JavaScript runtime environment. It stores callback functions that are waiting to be executed by the event loop.

## What is the `WHERE` clause in SQL?

The `WHERE` clause is used to filter rows based on a specified condition.

## What is the `HAVING` clause in SQL?

The `HAVING` clause is used to filter grouped results after the `GROUP BY` operation.

## Explain `let`, `var`, and `const` in hoisting.

`var` is hoisted and initialized with `undefined`. `let` and `const` are also hoisted, but they remain in the Temporal Dead Zone until their declaration is reached.

## Explain `Promise.allSettled()`.

`Promise.allSettled()` waits for all promises to complete, whether they are fulfilled or rejected. It returns the result of every promise.

## How do you consume an existing promise?

An existing promise can be consumed using `.then()` for a successful result and `.catch()` for handling errors. It can also be consumed using `async/await`.

## Why do we use promises?

Promises are used to handle asynchronous operations. They make asynchronous code easier to manage and provide better error handling and chaining.

## What is the difference between `map()` and `forEach()`?

`map()` creates and returns a new array after applying a function to each element. `forEach()` only executes a function for each element and does not return a new array.

## What are the problems with callback hell?

Callback hell makes code difficult to read, understand, maintain, and debug. It can also make error handling more complicated.

## What is the difference between `.then()` and `.catch()`?

`.then()` is used to handle a successfully fulfilled promise. `.catch()` is used to handle a rejected promise or an error.

## What is Node.js?

Node.js is a JavaScript runtime environment that allows JavaScript to run outside the browser. It is built on the V8 JavaScript engine.