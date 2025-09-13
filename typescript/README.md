# TypeScript

This section contains TypeScript code examples, utilities, and other information.
It covers both TypeScript and JavaScript.

## General Information

- `document.cookie = ${SIDEBAR_COOKIE_NAME}=${openState}; path=/; max-age=${SIDEBAR_COOKIE_MAX_AGE}` -> This line of code will not overwrite all cookies; it only creates or updates the cookie with the name `SIDEBAR_COOKIE_NAME` for the current domain and specified path (`/` in this case, meaning site-wide). Other cookies remain untouched, since `document.cookie` doesn’t replace the whole cookie store — it just adds or updates the one you specify. If a cookie with the same name, path, and domain already exists, it will be overwritten; otherwise, a new one is created.

- In TypeScript, __brand (or similar naming like _brand or brand) is a common pattern for branding types — a way to create nominal types in a structurally typed system. By default, TypeScript only checks the shape of a type (structural typing), so two types with the same structure are interchangeable. Adding a private or fake property like __brand: "UserId" to a type (often via an intersection) makes it unique, so even if it’s just a string underneath, UserId won’t be assignable to a plain string or to another branded type like OrderId. The __brand field doesn’t exist at runtime (it’s never assigned), but it helps the compiler enforce stricter type distinctions.
  - `type PositiveNumber = number & { __brand: 'PositiveNumber' };`

- The `toISOString()` method in JavaScript returns a string representation of a date in ISO 8601 format, which is based on UTC (Coordinated Universal Time).

- `Promise.allSettled` is generally better than manually looping through asynchronous tasks when you want to run them in parallel and collect both successful and failed results. It provides a clean, structured way to handle each outcome without writing custom logic, and it's much faster than sequentially awaiting each promise in a loop. Manual looping is only better if you need sequential execution or dependencies between operations.

- In TypeScript, `undefined` means a variable has been declared but not assigned a value (or a property is missing), while `null` is an explicit assignment that represents "no value" or intentional emptiness; both are primitive values but behave differently in checks. By contrast, `unknown` is a type, not a value — it’s a safer counterpart to `any` that means "the type is not known yet," so you must narrow it (with type guards or assertions) before using it. In short: `undefined` = uninitialized/missing, `null` = explicitly empty, and `unknown` = a type that forces type safety until clarified.

- Enums are just a union of string literal values under the hood ("create" | "delete" | "..."). Thus, you can use `Exclude` on it (not `Omit` - this is for objects) and you may also use enums as types (like `AccessOperation` as operation's type and then e.g. use `AccessOperation.CREATE` to check for specific used values in the function's body).

- JavaScript is single-threaded and uses an event loop to handle concurrency. When you perform actions like fetching data from websites, the actual network work is handled by the runtime (Node.js or the browser), and JavaScript just waits for results via callbacks, promises, or async/await. This means many requests can be in flight at once, but the JavaScript code that processes results runs one piece at a time. So JS gives you concurrency, but not true parallelism unless you use extra features like worker threads. Go, on the other hand, was designed with concurrency and parallelism in mind. It uses goroutines, which are lightweight threads managed by the Go runtime. The runtime schedules thousands of goroutines onto a pool of operating system threads, allowing tasks to run in parallel across multiple CPU cores. So if you scrape multiple websites in Go, your goroutines can truly execute simultaneously, not just take turns like in JS. In short: JavaScript’s concurrency is cooperative (event loop, async I/O, one main thread), while Go’s concurrency can be parallel (goroutines scheduled across threads). Both can handle many tasks efficiently, but Go has built-in support for scaling across CPU cores, whereas JS focuses on non-blocking async execution in a single thread.

- Worker threads are a way for JavaScript to achieve parallelism by running code on multiple threads, instead of relying only on the single-threaded event loop. Normally, JavaScript is single-threaded, so even though it can handle many asynchronous I/O tasks efficiently, it can’t spread CPU-heavy work across multiple cores without blocking the main thread. In Node.js, worker threads let you spin up additional threads, each with its own event loop and memory space. You communicate with these workers through message passing, which allows them to run tasks in parallel while the main thread stays free for other work. Similarly, in browsers, Web Workers serve the same purpose: they run code in the background so the UI stays responsive. Unlike Go’s lightweight goroutines, worker threads are tied to actual OS threads and therefore have more overhead. Still, they are very useful for tasks like image processing, cryptography, or parsing large datasets — basically anything CPU-bound that would otherwise block the single-threaded event loop. So in short: worker threads bring true parallelism to JavaScript, but they’re heavier than Go’s concurrency model and are typically reserved for CPU-intensive work rather than everyday async operations.

- Question: In JavaScript, does creating a worker thread mean starting a full OS thread, while in Go I can create many lightweight goroutines that share OS threads and automatically scale across CPU cores if needed?
  - Answer: Exactly. A JavaScript worker thread is tied directly to an OS thread, which makes it relatively expensive to create and limits how many you can realistically run at once. By contrast, Go’s goroutines are lightweight and managed by the Go runtime scheduler. Many goroutines can be multiplexed onto a smaller set of OS threads, and if the workload grows, the runtime spreads them across multiple threads and CPU cores. This makes goroutines far more scalable for handling massive concurrency than JavaScript workers.

- In JavaScript, concurrency primarily comes from its single-threaded event loop model. Although JavaScript executes code on a single main thread, it can handle multiple tasks seemingly at the same time by using asynchronous operations. When a task involves waiting—like fetching data from a server or reading a file, JavaScript doesn't block the thread; instead, it registers a callback or promise to resume later and continues running other code. This lets multiple tasks make progress without waiting for each other, which is concurrency: managing multiple tasks by quickly switching between them. However, this concurrency in JavaScript is not parallelism because only one task is actually executing at any given moment on the main thread. To achieve true parallelism—where tasks literally run at the same time on multiple CPU cores—you need to use Web Workers in the browser or Worker Threads in Node.js. These run scripts in separate threads, allowing multiple pieces of code to execute simultaneously, independently from the main event loop. So, JavaScript’s concurrency model enables efficient handling of many tasks by non-blocking asynchronous operations, but parallelism requires explicit use of multiple threads or processes. This design balances simplicity (single-threaded execution) with responsiveness (async concurrency), while still giving developers the option to exploit parallelism when needed.

- Primitives (numbers, strings, booleans, etc.) are passed by value when passing them as arguments to a function, so inside the function you get a copy. Modifying the parameter does not affect the original variable - `let number = 100; ... increment(number); ... // the original "number" is still unchaged`

- The values of objects (arrays, objects, functions, etc.) are passed as reference to the object when passing them as arguments to a function, but the reference itself is passed by value. That means inside the function you can modify the object's properties, and those changes will reflect outside the function - `let data = { count: 100 }; ... modify(data); ... // the original "data" was modified afterwards`


## Code Examples

### Tanstack Table: globalFilterFn

```ts
const globalFilterFn: FilterFn<Data> = (row, _, filterValue) => {
  if (!filterValue) return true // No filter applied

  // then do some matching with the help of the tableColumns (loop through them, get the value of each row's column with getValue and the table columns' id (you get that from the table column in the loop) and then compare the filterValue with the rowValue and if they match, we want to show the row (if not, it's filtered out) -> if at lest one column of a row matches, we want to show the whole row (use `some` to loop through tableColumns and then return this condition in the end with other conditions if needed))
  // Use table.setGlobalFilter for manually setting the global filter, you can pass whatever in there (doesn't just need to be a string for global search term, you can pass an object in there, too (but you will need a custom globalFilterFn))
  // Have in mind to check if the columns have proper values assigned with the accessFn (or called similarly), this needs to match, what you are trying to filter, any values in cell won't be recognized for filtering)
}
```

### Example seed script in Payload CMS
```ts
import payloadConfig from '@/payload.config'
import { getPayload } from 'payload'
import { seedWebsites } from './websites/seedWebsites'

/**
 * This is a base seed script that will get the application's payload setup and use it for any seed scripts
 * This script is setup so you can run it directly via 'payload run ./seed.ts'
 * The 'payload run' is special to Payload CMS and helps setting up the option to use getPayload
 * 
 * In the package.json you can add '"seed": "payload run ./src/path_to_seeder/seed.ts"' to run this script
 * It will run this file where it sees that the seed function is invoked, get the payload setup and run the seedEntitiesScript
 * In the onInit in the payload.config.ts you would not add this script, but a different base script where you get payload as argument or call seedEntitiesScript and other seeder scripts directly in there
 */
async function seed() {
  try {
    const payload = await getPayload({ config: payloadConfig })

    await seedEntitiesScript(payload)
  } catch {
    process.exit(1)
  }

  process.exit(0)
}

await seed()
```

### Custom Error with Type-Safety

```ts
import { APIError, CollectionSlug, GeneratedTypes } from 'payload'

type Collections = GeneratedTypes['collections']
type Resource = CollectionSlug

export class NotFoundError<R extends Resource, K extends keyof Collections[R]> extends APIError {
  resource: R
  findWith: { key: K; value: Collections[R][K] }

  constructor(
    resource: R,
    findWith: { key: K; value: Collections[R][K] },
    meta?: Record<string, unknown>,
  ) {
    super(
      `document of '${resource}' with ${String(findWith.key)} '${String(findWith.value)}' not found`,
      404,
      {
        resource,
        findWith,
        ...meta,
      },
    )
    this.resource = resource
    this.findWith = findWith
  }
}
```
