# TypeScript

This section contains TypeScript code examples, utilities, and other information.
It covers both TypeScript and JavaScript.

## General Information

- Primitives (numbers, strings, booleans, etc.) are passed by value when passing them as arguments to a function, so inside the function you get a copy. Modifying the parameter does not affect the original variable - `let number = 100; ... increment(number); ... // the original "number" is still unchaged`

- The values of objects (arrays, objects, functions, etc.) are passed as reference to the object when passing them as arguments to a function, but the reference itself is passed by value. That means inside the function you can modify the object's properties, and those changes will reflect outside the function - `let data = { count: 100 }; ... modify(data); ... // the original "data" was modified afterwards`
