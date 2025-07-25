# TypeScript

This section contains TypeScript code examples, utilities, and other information.
It covers both TypeScript and JavaScript.

## General Information

- In JavaScript, concurrency primarily comes from its single-threaded event loop model. Although JavaScript executes code on a single main thread, it can handle multiple tasks seemingly at the same time by using asynchronous operations. When a task involves waiting—like fetching data from a server or reading a file, JavaScript doesn't block the thread; instead, it registers a callback or promise to resume later and continues running other code. This lets multiple tasks make progress without waiting for each other, which is concurrency: managing multiple tasks by quickly switching between them. However, this concurrency in JavaScript is not parallelism because only one task is actually executing at any given moment on the main thread. To achieve true parallelism—where tasks literally run at the same time on multiple CPU cores—you need to use Web Workers in the browser or Worker Threads in Node.js. These run scripts in separate threads, allowing multiple pieces of code to execute simultaneously, independently from the main event loop. So, JavaScript’s concurrency model enables efficient handling of many tasks by non-blocking asynchronous operations, but parallelism requires explicit use of multiple threads or processes. This design balances simplicity (single-threaded execution) with responsiveness (async concurrency), while still giving developers the option to exploit parallelism when needed.

- Primitives (numbers, strings, booleans, etc.) are passed by value when passing them as arguments to a function, so inside the function you get a copy. Modifying the parameter does not affect the original variable - `let number = 100; ... increment(number); ... // the original "number" is still unchaged`

- The values of objects (arrays, objects, functions, etc.) are passed as reference to the object when passing them as arguments to a function, but the reference itself is passed by value. That means inside the function you can modify the object's properties, and those changes will reflect outside the function - `let data = { count: 100 }; ... modify(data); ... // the original "data" was modified afterwards`

