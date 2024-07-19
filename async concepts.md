Here's the information organized in Markdown format as requested:

### Why Promises are Better than Callbacks

In JavaScript, we use callbacks to handle asynchronous operations by passing a function as an argument to another function. We rely on the callback function to execute once the asynchronous operation completes. However, this can lead to issues like callback hell, making the code difficult to read and maintain.

Promises provide a better way to handle asynchronous operations. Instead of passing a callback, we attach handlers to a promise object using `.then()`, `.catch()`, and `.finally()` methods. This approach helps to avoid callback hell and makes the code more readable and manageable.

### How JavaScript Executes Code

JavaScript is a synchronous, single-threaded language. Execution happens line by line and in order. The JavaScript engine uses a call stack to manage execution contexts, which are created and deleted as functions are invoked. This ensures the proper order of execution and manages the flow of function calls efficiently.

### Difference Between Sync and Async

- **Async (Asynchronous)**:
  - Allows operations or programs to run in parallel.
  - Non-blocking: Sends multiple requests to a server.
  - Increases throughput by running multiple operations simultaneously.

- **Sync (Synchronous)**:
  - Single-threaded: Only one operation or program runs at a time.
  - Blocking: Sends server requests one at a time, waiting for each to complete.
  - Slower and more methodical.

### Ways to Make Code Async

1. Callbacks
2. async/await
3. Promises

### Web APIs in JavaScript

In JavaScript, Web APIs (Application Programming Interfaces) are sets of pre-built functionalities provided by the browser or web environment. They allow your JavaScript code to interact with and manipulate various aspects of the browser and external services.

Examples:
- **DOM API**: Manipulates HTML and CSS elements on a webpage.
- **Fetch API**: Makes network requests to retrieve data from servers.
- **Geolocation API**: Accesses the user's location (with permission).
- **Local Storage & Session Storage**: Stores data locally in the user's browser.

### How Event Loops Work

- **Call Stack**: Keeps track of the currently executing function. Manages function invocation order.
- **Callback Queue**: Stores asynchronous operations (I/O, timers) callbacks.
- **Event Loop**: Checks the call stack and callback queue. Processes callbacks when the call stack is empty.
- **Execution**: Executes functions, handles asynchronous operations, and manages callback execution.
- **Repeat**: Continues checking the call stack and callback queue to maintain program flow.

### Callback Hell

Callback hell occurs when multiple callbacks are nested within each other, making the code hard to read and maintain. This can be resolved by using promises or async/await, which provide cleaner and more readable asynchronous code handling.

### Inversion of Control in Callbacks

Inversion of control in callbacks occurs when the control flow is passed to an external function or API through a callback function. This inverts the traditional flow of control where the main program dictates the sequence of operations.

### Creating a New Promise

You can create a new promise using the `Promise` constructor, which takes an executor function with `resolve` and `reject` parameters. These functions change the state of the promise.

### States of a Promise

- **Pending**: Initial state. Neither fulfilled nor rejected.
- **Fulfilled**: Operation completed successfully.
- **Rejected**: Operation failed.

### Consuming an Existing Promise

You can consume a promise using:
- `.then()`: Executes when the promise is fulfilled.
- `.catch()`: Executes when the promise is rejected.
- `.finally()`: Executes regardless of fulfillment or rejection.

### Chaining Promises Using `.then`

Promises can be chained using `.then()` to perform a series of asynchronous operations sequentially.

### Async Concepts

When an error is thrown inside a `.then` block:
- With a `.catch` block: The error is caught and handled.
- Without a `.catch` block: The error is unhandled, leading to a rejected promise.

### Using Promise-Based Functions

#### Promise.resolve(value)

Returns a resolved promise with the specified value.

```javascript
let promise = Promise.resolve('Success');

promise.then(value => {
  console.log(value); // Output: Success
});
```

#### Promise.reject(reason)

Returns a rejected promise with the specified reason.

```javascript
let promise = Promise.reject('Error');

promise.catch(error => {
  console.error(error); // Output: Error
});
```

#### Promise.all(promises) [fail fast]

Resolves when all promises in the array resolve, or rejects if any promise rejects.It will not wait for other promises it will `fail quickly` and return.

```javascript
Promise.all([promise1, promise2, promise3])
  .then(results => {
    console.log(results); // Output: ['Result 1', 'Result 2', 'Result 3']
  })
  .catch(error => {
    console.error(error);
  });
```

#### Promise.allSettled(promises)

Resolves when all promises in the array have settled (resolved or rejected), providing an array of results.It will wait for first seeking result and return it . if all of them fails then it will return an aggregate error of arrays.

```javascript
Promise.allSettled([promise1, promise2, promise3])
  .then(results => {
    console.log(results);
    // Output: [{ status: 'fulfilled', value: 'Result 1' }, { status: 'rejected', reason: 'Error 2' }, { status: 'fulfilled', value: 'Result 3' }]
  });
```

#### Promise.any(promises)

Resolves with the value of the first resolved promise, or rejects if all promises reject.

```javascript
Promise.any([promise1, promise2, promise3])
  .then(result => {
    console.log(result); // Output: Result 2 (first resolved promise)
  })
  .catch(error => {
    console.error(error);
  });
```

#### Promise.race(promises)

Resolves or rejects when the first promise in the array resolves or rejects.if it will be error it will return error and if it will be Settled it will return settled.

```javascript
Promise.race([promise1, promise2, promise3])
  .then(result => {
    console.log(result); // Output: Result 2 (first to resolve)
  })
  .catch(error => {
    console.error(error);
  });
```

These examples demonstrate how to effectively use and understand promise-based functions in JavaScript, providing efficient handling of asynchronous operations and improving code readability and maintainability.
