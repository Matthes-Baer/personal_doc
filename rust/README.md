# Rust

This section covers information about the programming language Rust.

## Useful Links

- [Most Important Information](https://doc.rust-lang.org/book/title-page.html)
- [Vectors under the hood (on the Stack (capacity, length, pointer) - potential re-allocation; on the Heap)](https://www.udemy.com/course/master-the-rust-programming-language/learn/lecture/44274774#overview)
- [Error propagation operator `?`](https://www.udemy.com/course/master-the-rust-programming-language/learn/lecture/44105998#overview)
- [Lifetime and Scope](https://www.udemy.com/course/master-the-rust-programming-language/learn/lecture/44416360#overview)
- [Trait Objects and Virtual Table](https://www.udemy.com/course/master-the-rust-programming-language/learn/lecture/45093215#overview)
- [Organizing Modules in Seperate Files (this and the next video)](https://www.udemy.com/course/master-the-rust-programming-language/learn/lecture/47092443#overview)
- [Deref Coercion](https://doc.rust-lang.org/book/ch15-02-deref.html#implicit-deref-coercions-with-functions-and-methods)
- [Reference Counting (Rc) and RefCell](https://www.udemy.com/course/autogpt-gpt4-code-writing-ai/learn/lecture/38251074#overview)
- [Reference Counting (Rc) with Weak](https://www.udemy.com/course/autogpt-gpt4-code-writing-ai/learn/lecture/38251700#overview)

## Useful Rust Lines

- Create new Rust project: `cargo new project_name`
- Add a crate to your project (with the feature `full` in this example): `cargo add crate_name --features full`
- Convert a number to it's binary representation: `let binary_repr = format!("{:b}", n);`
- Convert a binary number to it's decimal representation: `match isize::from_str_radix(&reversed_binary, 2) { ... handle Ok() and Err() ... }`
- Get sum from all Vector elements: `let sum: i32 = (1..=n).collect().iter().sum();`
- Get product from all Vector elements: `let product: i32 = (1..=n).collect().iter().product();`
- Setup Diesel: `diesel setup`
- Create Diesel migration: `diesel migration generate NAME`
- Run Diesel migration: `diesel migration run`
- Redirect standard console messages to another file: `cargo run > console.txt`
- Redirect only the console error messages to another file: `cargo run 2> errors.txt`
- Shortcut for strings with escape sequences (instead of having to escape with \\ for each occurence, for example): `let text = r#"C:\Program Files\PostgreSQL\16\lib"#`
- Create an array with one value for all entries and with a specific size: `let array = [0_u8; 256];`
- Print the memory location of a variable (also works for references): `println!("{:p}", some_variable);`
- Make use of [Clippy](https://github.com/rust-lang/rust-clippy): `cargo clippy`
- If Let with @ symbol (if y is within the inclusive range of 1..=4): `if let (_, y @ 1..=4) = (4, 2) { ... }`
- Declare and Initialize a Vector with some initial values: `let vector_variable: Vec<i32> = Vec::from([1, 2, 3])` or `let vector_variable: Vec<i32> = vec![1, 2, 3]`
- Prepend elements to a vector: `vec.splice(0..0, elements_to_prepend)` or create a new vector and use `extend()` | or use a VecDeque for such situations
- Modify an existing key-value pair of a HashMap or insert if not already existing: `hashmap_variable.entry("some_key").and_modify(|value| *value += 1).or_insert(1);`
- Create a Type: `type Point = (i32, i32);`
- Loop through a collection with references (borrowing): `for x in collection.iter() { ... }`
- Loop through a collection with values (taking ownership and consuming the collection (for arrays it yields references to elements)): `for x in collection.into_iter() { ... }`
- Use `dbg!()` instead of `println!()` for debugging purposes to avoid writing too much (since `dbg!()` will pretty print like a vector directly)

Only types with the `PartialOrd` AND `Copy` traits are allowed for this function

## Useful Methods (not exhaustive)

### 📚 Vec<T> (Vector)

| Method                   | Description                             |
|--------------------------|-----------------------------------------|
| `.len()`                 | Get number of elements                  |
| `.is_empty()`            | Check if empty                          |
| `.push(value)`           | Append element                          |
| `.pop()`                 | Remove and return last element          |
| `.insert(index, value)`  | Insert at index                         |
| `.remove(index)`         | Remove at index                         |
| `.clear()`               | Remove all elements                     |
| `.get(index)`            | Safe indexing → `Option<&T>`            |
| `[index]`                | Direct indexing (panics if out-of-bounds) |
| `.contains(&val)`        | Check if value exists                   |
| `.sort()` / `.sort_by()` | Sort in-place                           |
| `.reverse()`             | Reverse in-place                        |
| `.truncate(n)`           | Keep only first `n` elements            |
| `.retain(f)`             | Keep elements matching condition        |
| `.resize(n, val)`        | Resize with default value               |
| `.extend(iter)`          | Append elements from another iterator   |
| `.split_at(index)`       | Split into two slices                   |
| `.clone()`               | Deep copy                               |
| `.iter()`                | Immutable iterator                      |
| `.iter_mut()`            | Mutable iterator                        |
| `.into_iter()`           | Consuming iterator                      |

- Vec::with_capacity() - minimize memory re-allocations by specifiying a specific capacitiy of the vector at the start (the capacity on the Stack is larger than the actual current vector length; If the vector length would exceed the capacity, a re-allocation occurs (a new pointer is assigned in the Stack which points to different location on the Heap compared to the original used pointer) (such re-allocations can be minimized by specifiying a capacity by yourself instead of letting it increase on its own)) -> helpful for situations where you have information on how many elements a vector will hold in the future.


### 🧵 String and &str

#### 🔤 Shared Methods

| Method                   | Description                             |
|--------------------------|-----------------------------------------|
| `.len()`                 | Length in bytes                         |
| `.is_empty()`            | Check if empty                          |
| `.chars()`               | Iterator over characters                |
| `.bytes()`               | Iterator over bytes                     |
| `.split(delim)`          | Split by delimiter                      |
| `.split_whitespace()`    | Split by whitespace                     |
| `.trim()`                | Remove surrounding whitespace           |
| `.replace(from, to)`     | Replace substrings                      |
| `.contains(substr)`      | Check if contains substring             |
| `.starts_with()`         | Check prefix                            |
| `.ends_with()`           | Check suffix                            |
| `.find()`, `.rfind()`    | Find index of match                     |
| `.to_lowercase()`        | Lowercase version                       |
| `.to_uppercase()`        | Uppercase version                       |

#### 🧵 String-only

| Method                   | Description                             |
|--------------------------|-----------------------------------------|
| `.push(char)`            | Append character                        |
| `.push_str(&str)`        | Append string slice                     |
| `.clear()`               | Clear the string                        |
| `.as_str()`              | Convert to `&str`                       |
| `.into_bytes()`          | Convert to `Vec<u8>`                    |
| `.capacity()`, `.reserve()` | Manage memory                        |


### 🔠 char

| Method                   | Description                             |
|--------------------------|-----------------------------------------|
| `.is_alphabetic()`       | Is letter                               |
| `.is_numeric()`          | Is digit                                |
| `.is_alphanumeric()`     | Is letter or digit                      |
| `.is_whitespace()`       | Is space/tab/newline                    |
| `.to_digit(radix)`       | Convert to number (base)                |
| `.to_uppercase()`        | Convert to uppercase                    |
| `.to_lowercase()`        | Convert to lowercase                    |


### 🔢 Numbers (i32, u32, usize, f64, etc.)

| Method                   | Description                             |
|--------------------------|-----------------------------------------|
| `.abs()`                 | Absolute value                          |
| `.pow(exp)`              | Power                                   |
| `.sqrt()` (f64 only)     | Square root                             |
| `.max(other)`            | Max of two                              |
| `.min(other)`            | Min of two                              |
| `.clamp(min, max)`       | Clamp within range                      |
| `.is_nan()`              | Check if NaN                            |
| `.is_infinite()`         | Check if infinite                       |
| `.to_string()`           | Convert to string                       |
| `.checked_add()`, etc.   | Overflow-safe math                      |


### 🗺️ HashMap<K, V>

| Method                                | Description                                      |
|--------------------------------------|-------------------------------------------------|
| `HashMap::new()`                     | Create an empty HashMap                          |
| `.insert(key, val)`                  | Add or overwrite an entry                        |
| `.get(&key)`                        | Get value by key → `Option<&V>`                  |
| `.get_mut(&key)`                    | Get mutable reference to value                   |
| `.remove(&key)`                     | Remove an entry                                  |
| `.contains_key(&key)`               | Check if key exists                              |
| `.entry(key).or_insert(val)`        | Insert if key doesn't exist                      |
| `.entry(key).or_insert_with(func)`  | Lazily insert with function                      |
| `.len()`                            | Number of key-value pairs                        |
| `.is_empty()`                      | Check if empty                                   |
| `.clear()`                         | Remove all entries                               |
| `.clone()`                         | Deep copy of the map                             |
| `.iter()`                         | Iterate as `(&K, &V)`                            |
| `.iter_mut()`                     | Mutable iteration as `(&K, &mut V)`              |
| `.into_iter()`                    | Consume map → `(K, V)`                            |
| `.keys()`                        | Iterator over keys                               |
| `.values()`                      | Iterator over values                             |
| `.values_mut()`                  | Mutable iterator over values                     |
| `.retain(|k, v| cond)`           | Retain only matching entries                     |
| `.extend(iter)`                  | Add entries from another iterable                |
| `.capacity()`                    | Current allocation capacity                      |
| `.with_capacity(n)`              | Create with pre-allocated capacity               |
| `.shrink_to_fit()`               | Shrink capacity to fit size                      |
| `.drain()`                      | Remove and iterate all elements                  |
| `.default()`                    | Create empty map with `Default`                  |


### 🔁 Iteration

| Method               | Description                                  |
|----------------------|----------------------------------------------|
| `.next()`            | Return the next element                       |
| `.collect()`         | Gather items into a collection (Vec, HashMap, etc.) |
| `.map(f)`            | Transform each element using closure `f`    |
| `.filter(f)`         | Keep elements where closure `f` returns true|
| `.filter_map(f)`     | Filter and map in one step                    |
| `.fold(init, f)`     | Reduce elements to a single value             |
| `.sum()`             | Sum all elements (requires `Sum` trait)       |
| `.product()`         | Multiply all elements                          |
| `.enumerate()`       | Yield `(index, element)` pairs                 |
| `.zip(other)`        | Combine with another iterator                  |
| `.chain(other)`      | Append another iterator                        |
| `.take(n)`           | Take first `n` elements                        |
| `.skip(n)`           | Skip first `n` elements                        |
| `.rev()`             | Reverse iterator (if supported)                |
| `.count()`           | Count number of elements                       |
| `.find(f)`           | Find first element matching predicate `f`    |
| `.any(f)`            | Check if any element matches predicate `f`   |
| `.all(f)`            | Check if all elements match predicate `f`    |
| `.position(f)`       | Get index of first match for predicate `f`   |
| `.inspect(f)`        | Run closure `f` on each element for debugging |
| `.flatten()`         | Flatten nested iterators                       |
| `.copied()`          | Copy elements (for references)                 |
| `.cloned()`          | Clone elements (for references)                |




## Useful Crates (`Cargo.toml`)

- actix-web = "4.6.0"
- anyhow = "1.0.86"
- diesel = { version = "2.2", features = ["postgres", "r2d2"] }
- dotenv = "0.15.0"
- reqwest = { version = "0.12.4", features = ["json"] }
- serde_json = "1.0.117"
- serde = { version = "1.0", features = ["derive"] }
- tokio = { version = "1.38.0", features = ["full"] }
- tokio_schedule = "0.3.1"
- env_logger = "0.11.3"
- log = "0.4.21"
- async-trait = "0.1.68"
- actix-cors = "0.6.4"
- tonic (Rust gRPC client/server framework - Handles gRPC communication, HTTP/2, protobuf encoding/decoding; required for gRPC calls including Arrow Flight)
- arrow (Apache Arrow data structures & utilities - Manipulates Arrow in-memory columnar data (schema, arrays, serialization, etc.))
- arrow-flight (Protocol definitions and client/server code for Apache Arrow Flight over gRPC - Builds on tonic; defines RPC methods for efficient Arrow data transport)

Also:

- [r2d2 (see features of diesel above)](https://crates.io/crates/r2d2)

## Important Attributes

- #[derive(...)]: Automatically generates trait implementations for types (e.g., Debug, Clone, PartialEq).
- #[cfg(...)]: Conditional compilation, only compiles the code if a specific condition is met (e.g., test, debug_assertions).
- #[cfg(test)]: Marks code (e.g., test modules) to only be compiled during testing.
- #[test]: Marks a function as a test function, which the test runner will execute.
- #[allow(...)]: Suppresses specific compiler warnings (e.g., unused_variables, dead_code).
- #[warn(...)]: Turns specific compiler warnings on (e.g., deprecated, unused_imports).
- #[deny(...)]: Treats specific warnings as errors, halting compilation.
- #[inline]: Suggests to the compiler that a function should be inlined for performance.
- #[non_exhaustive]: Prevents users of a type (usually enums or structs) from matching on all variants or fields, allowing future changes.
- #[must_use]: Marks a function's return value or a type as something that should not be ignored.
- #[repr(...)]: Specifies how a struct or enum should be represented in memory (e.g., C, transparent).
- #[panic_handler]: Defines a custom panic handler for no_std environments.
- #[no_std]: Disables linking to the standard library, often used for embedded or bare-metal programming.
- #[macro_export]: Marks a macro to be exported from the current crate for use in other crates.
- #[doc(...)]: Adds documentation comments or controls the visibility of documentation (e.g., hidden to hide an item from docs).
- #[ignore]: Marks a test function to be ignored by default during testing.
- #[inline(always)]: Strongly suggests that a function should always be inlined.
- #[global_allocator]: Defines a global memory allocator for the program.
- #[tokio::main]: Marks an async function as the entry point for a Tokio-based application.
- #[serde(...)]: Used with the serde crate to customize (de)serialization behavior of types.

## Important Traits

- **Debug**: Allows formatting a type using {:?} for debugging purposes.
- **Add**: In Rust, the Add trait is used to overload the + operator, allowing custom behavior when adding two values of a type. Due to this trait you are able to calculate like this: `sum = i32 + &i32` (this is valid even though there are two different types used).
- **Display**: Provides user-facing string formatting, typically for error messages or final output using {}.
- **Clone**: Enables the type to be cloned explicitly using .clone() (deep copy).
- **Copy**: Allows types to be copied implicitly instead of moved. Must be a simple, stack-only type (like numbers or small structs).
- **PartialEq**: Enables equality comparisons (==, !=) between instances, comparing fields.
- **Eq**: A stricter version of PartialEq, indicating that all values of the type are comparable (no partial comparisons).
- **PartialOrd**: Allows partial ordering comparisons (<, >, <=, >=), for types where not all values can be ordered.
- **Ord**: Defines a total ordering for types, allowing comparisons (<, >, etc.) where all values can be ordered.
- **Hash**: Allows types to be used as keys in hash maps by providing a hashing mechanism.
- **Default**: Provides a default value for the type, which can be created with Default::default().
- **Serialize** (Serde): Enables serialization of a type into formats like JSON or YAML.
- **Deserialize** (Serde): Allows deserialization of a type from formats like JSON or YAML.
- **AsRef**: Converts a type to a reference of another type, usually used for converting to slices or strings.
- **AsMut**: Converts a type to a mutable reference of another type.
- **From**: Provides a way to create an instance of a type from another type.
- **Into**: Allows converting a type into another type, the inverse of From.
- **TryFrom**: Allows fallible conversions from one type to another (with possible errors).
- **TryInto**: The fallible counterpart to Into, allowing type conversion with error handling.
- **Iterator**: Enables an object to yield a sequence of values, allowing it to be used in for loops.
- **Queryable** (Diesel): Allows a type to be built from database query results.
- **Insertable** (Diesel): Enables a type to be inserted into a database table.
- **Identifiable** (Diesel): Marks a type as having a primary key for database use.
- **AsChangeset** (Diesel): Allows updating database rows with a type.
- **FnOnce**: This trait allows a closure to consume the variables it captures from its environment. After being called once, a `FnOnce` closure cannot be called again as the environment has been consumed.
- **FnMut**: If a closure does not consume its environment, it can also implement the `FnMut` trait. With this trait a closure can be called multiple times and can mutate the environment.
- **Fn**: If a closure does not mutate its environment, it can also implement the `Fn` trait. This means that the closure can be called multiple times without mutation the environment.

## General Information

- The **mod** keyword declares a module. Used to tell Rust to look for the corresponding file or directory (like `mod routes` or `mod services` in the `main.rs` file).
- The **use** keyword brings items into scope, allowing you to use them without fully qualifying their paths.
- Use **pub** to make functions, structs, or modules public. Without pub, items are private to the module.
- Use **pub use** to re-export items, making them accessible through the parent module.
- By implementing a "Trait" for a type, that type gains the ability to utilize the methods defined by the trait. This enables **polymorphism**, where different types can be treated interchangeably as long as they implement the same trait.
- Rust provides automatic dereferencing for method calls and field access when you have a reference to an object, such as a tuple, or an object of a struct or enum (so you don't have to explicitly use _\*_ for derefencing but can just use **my_tuple.0 += 1** while **my_tuple** would be a reference in this case).
- The error propagation operator `?` allows you to return an error from a function if a `Result` or `Option` is `Err` or `None`, respectively, simplifying error handling. This will also make the `Ok` or `Some` value responses directly available. This way, you only have to handle the `Err` and `None` in one parent function with `match` or `if let` or similar. Without this operator, you would need to handle each `Result` or `Option` case with `match` or `if let` or similar in all child functions which would create a lot of boilerplate code. Apply the `?` operator to the end of the calling expression to use it.
- **Monomorphization** in Rust is a compilation process where generic functions and types are specialized for their specific types at compile time. This means that for each concrete type used with a generic function or type, Rust generates a separate version of that function or type, tailored specifically to the concrete type. The specialized code can be as efficient as hand-written code for each type since there are no dynamic type checks or runtime polymorphism (no additional runtime overhead). If many different types are used with a generic, it can lead to increased binary size, as separate versions are created for each type.
- When working with Generic Structs, you may use multiple `impl` blocks to declare generic methods and associated functions, like `impl<T> My_Struct<T> { ... }` (you can also use `impl<T: Copy> ...` to indicate that the used type needs to include the Copy trait), while having other blocks like `impl My_Struct<i32> { ... }` or `impl My_Struct<&str> { ... }` to declare methods and associated functions which only work for those specific types.
- Enums in Rust are much more powerful and versatile than in TypeScript. For example, you may add methods to enums. Such enums are helpful for cases where you have multiple shapes, for example, like `Rectangle` or `Circle`. Instead of having multiple classes for each shape (in JavaScript), you may create one enum that holds those shape states and implements corresponding methods to calculate the area of each shape, for example.
- There are lifetime elision rules which help specifiying lifetimes (it's not something programmers need to follow, they are automatically applied): **1.** The first rule of lifetime elision is specifically for input lifetimes. Each parameter that is a reference gets its own lifetime parameter. **2.** If there is exactly one input lifetime parameter, that lifetime is assigned to all output lifetime parameters. **3.** If there are multiple input lifetime parameters, but one of them is `&self` or `&mut self` as part of a method, the lifetime of `self` is assigned to all ouput lifetime parameters.
- `cargo` is Rust's package manager with functionality like `cargo build --release`, `cargo fmt`, `cargo update`, and many more.
- Rust oftentimes dereferences under the hood (Deref Coercion), so that you don't have to explicitely use the `*` character (when printing, for example). In other cases where you have like a mutable reference to some value and try to change that value with the reference, you would have to dereference the reference in order actually be able to change the value (this will by the way change the underlying value, effectively also changing the corresponding reference's value).
  - Rust's Deref Coercion is a feature that automatically converts a reference from one type to another when needed, as long as the first type implements the Deref trait.
- HashSet (In JavaScript, you would use a Set):
  - Unordered
  - Fastest for insert, remove, and lookup (average-case O(1))
  - Uses a hash function
  - Order is not guaranteed
  - Ensures deduplicating (removing duplicates)
  - Use when: you need fast set operations and don’t care about order.
  - You can pass a vector with duplicates to a HashSet type like `let set: HashSet<_> = v.into_iter().collect();` to deduplicate the vector and create a HashSet from it.
- BTreeSet:
  - Ordered (sorted)
  - Slower than HashSet (O(log n) operations)
  - Backed by a B-tree
  - Iteration is in sorted order
  - Ensures deduplicating (removing duplicates)
  - Use when: you need the elements in order (e.g. for sorted output).


## Code Examples

### Arc, Mutex, Concurrency

```rs
use std::sync::{Arc, Mutex};
use std::thread;
use std::time::{Duration, Instant};

fn main() {
    // Simulated database data
    let db_data = vec!["id1", "id2", "id3", "id4", "id5"];

    // Shared vector wrapped in Arc (atomic reference count) and Mutex for safe access across threads
    let results = Arc::new(Mutex::new(Vec::new()));

    let start = Instant::now(); // Start timer

    // Vector to hold thread handles so we can join later
    let mut handles = vec![];

    for i in 0..db_data.len() {
        let results = Arc::clone(&results); // Clone Arc pointer for each thread
        let data = db_data[i];               // Copy current data

        // Spawn a new thread to simulate DB call
        let handle = thread::spawn(move || {
            thread::sleep(Duration::from_secs(2)); // Simulate delay

            // Lock the mutex to get mutable access to results
            let mut res = results.lock().unwrap();
            res.push(data); // Append result safely
        });

        handles.push(handle);
    }

    // Wait for all threads to finish
    for handle in handles {
        handle.join().unwrap();
    }

    // Print total execution time
    println!("Total execution time: {:?}", start.elapsed());

    // Lock results to print them
    let res = results.lock().unwrap();
    println!("The results are: {:?}", *res);
}
```

### Sort with Priority Mapping and Tiebreaker (Double Sorting)

```rs
fn main() {
    let mut data = vec![
        ("Zeta".to_string(), "pharmacy".to_string()),
        ("Alpha".to_string(), "grocery".to_string()),
        ("Echo".to_string(), "electronics".to_string()),
        ("Delta".to_string(), "electronics".to_string()),
        ("Beta".to_string(), "restaurant".to_string()),
    ];

    let priority = |line: &str| -> usize {
        match line {
            "electronics" => 0,
            "grocery" => 1,
            "pharmacy" => 2,
            "restaurant" => 3,
            _ => usize::MAX,
        }
    };

    data.sort_by(|a, b| {
        let pri_cmp = priority(&a.1).cmp(&priority(&b.1));
        if pri_cmp == std::cmp::Ordering::Equal {
            a.0.cmp(&b.0) // tiebreaker: sort by first field lexicographically
        } else {
            pri_cmp
        }
    });

    for (code, line) in &data {
        println!("{} - {}", code, line);
    }
}

...

Delta - electronics
Echo - electronics
Alpha - grocery
Zeta - pharmacy
Beta - restaurant
```

_What the `cmp` does:_

`let pri_cmp = priority(&a.1).cmp(&priority(&b.1));`

This uses the cmp method from Rust's Ord trait, which compares two values and returns one of:
- Ordering::Less
- Ordering::Equal
- Ordering::Greater

```rs
priority("electronics") == 0
priority("restaurant")  == 3

...

0.cmp(&3) // = Ordering::Less
```

_This means:_
electronics < restaurant - so, `a.1` will come before `b.1` in the sorted list. `a` is considered "smaller" than `b`.

If you would reverse the compare (`3.cmp(&0) = Ordering::Greater`): restaurant > electronics - restaurant also comes after electronics in sort order.

### [Two Sum](https://leetcode.com/problems/two-sum/description/)

```rs
use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut map = HashMap::new();
        for (i, num) in nums.iter().enumerate() {
            let pair = target - num;
            if let Some(index) = map.get(&pair) {
                return vec![i as i32, *index as i32];
            }
            map.insert(num, i);
        }
        vec![0, 0]
    }
}
```

### Extend Vectors

```rs
    for (x_idx, x_val) in digits.iter().enumerate() {
        let second_values = &digits[x_idx + 1..];

        // Start with one value and then add more values to the end from a slice
        let mut forward = vec![*x_val];
        forward.extend_from_slice(second_values);

        // Similar as above, but reversed and with "extend()" instead of "extend_from_slice()"
        let mut reversed = vec![*x_val];
        reversed.extend(second_values.iter().rev());
    }
```


### Find Closest

```rs
use std::cmp::Ordering;
use std::u32;

impl Solution {
    pub fn find_closest(x: i32, y: i32, z: i32) -> i32 {
        let a = x.abs_diff(z);
        let b = y.abs_diff(z);
        match u32::cmp(&a, &b) {
            Ordering::Less => 1,
            Ordering::Equal => 0,
            Ordering::Greater => 2,
        }
    }
}
```

### Dereferencing via pattern matching or manually dereferencing

`vowels.iter()` gives you an iterator over &char (references to chars).

_1. version (pattern matching):_

```rs
if vowels.iter().any(|&v| s.starts_with(v))
```

- |&v| pattern-matches and dereferences each &char into a char.
- v is of type char inside the closure.
-> This is destructuring the reference directly in the closure parameter - via pattern matching.

_2. version (manual dereferencing):_

```rs
if vowels.iter().any(|v| s.starts_with(*v))
```

- v is of type &char (reference to a char).
- *v dereferences the &char into a char before passing it to starts_with.
-> This is manual dereferencing inside the closure body.

_Which one should you use?_
Both are correct and idiomatic. Use whichever is clearer to you. For beginners, *v may feel more explicit, while |&v| is more concise and idiomatic once you're comfortable with Rust's pattern matching.


### Converting Types

Instead of just casting like `x as usize` with x being of type `i32` before, you may want to use `try_into()` to have a proper type conversion:

```rs
use std::convert::TryInto;

fn main() {
    let x: i32 = 42;

    // Try to convert i32 to usize safely
    let y: usize = match x.try_into() {
        Ok(val) => val,
        Err(_) => {
            println!("Cannot convert negative or out-of-range value");
            return;
        }
    };

    println!("Converted value: {}", y);
}
```


### `.zip()` Method

`.zip()` pairs up elements from both iterators into tuples.

```rust
fn main() {
    let numbers = vec![1, 2, 3];
    let letters = vec!['a', 'b', 'c'];

    // Zip the two iterators together
    let zipped: Vec<(i32, char)> = numbers.iter().zip(letters.iter()).map(|(&n, &l)| (n, l)).collect();

    println!("{:?}", zipped);
    // Output: [(1, 'a'), (2, 'b'), (3, 'c')]
}
```

### Deserialization

```rs
use serde::{Deserialize};
use serde_json;

#[derive(Debug, Deserialize)]
struct Person {
    name: String,
    age: u8,
}

fn main() {
    let data = r#"{ "name": "Alice", "age": 30 }"#; // raw string literal - It lets you write strings without needing to escape backslashes or quotes, which is especially useful for things like JSON, regex patterns, file paths, etc.

    let person: Person = serde_json::from_str(data).unwrap();

    println!("{:?}", person);
}

// Output:
// Person { name: "Alice", age: 30 }
```

### for<'a>

_What does for<'a> mean?_
It makes the function generic over all lifetimes 'a. In other words, the function must be able to accept a reference with any lifetime, not just a specific one.

This shows up when you want to pass functions as parameters (or define function pointers) that are generic over lifetimes.

```rs
fn always_hello(_: &str) -> &'static str {
    "hello"
}

fn call_it(f: for<'a> fn(&'a str) -> &'static str) {
    println!("{}", f("whatever"));
}

fn main() {
    call_it(always_hello);
}
```

If you didn't use for<'a>, then the function pointer would expect a single, specific lifetime, which could restrict what kind of functions you can pass in.

### GET fetch with custom headers with reqwest

```rs
use reqwest; // 0.10.0
use tokio; // 0.2.6

#[tokio::main]
async fn main() -> Result<(), reqwest::Error> {
    let client = reqwest::Client::new();
    let res = client
        .get("https://www.rust-lang.org")
        .header("X-My-Custom-Header", "foo")
        .send()
        .await?;

    Ok(())
}
```

### into_inner()

The `into_inner()` will basically extract the inner part of the `web::Json<Task>` type that would be `Task`.

```rs
async fn create_task(app_state: web::Data<AppState>, task: web::Json<Task>) -> impl Responder {
  let mut db = app_state.db.lock().unwrap();
  db.insert(task.into_inner());
  let _ = db.save_to_file();
  HttpResponse::Ok().finish()
}
```

### Custom Error Handling in Actix-web

```rs

// Cargo.toml
[dependencies]
actix-web = "4.0"
thiserror = "1.0"
serde = { version = "1.0", features = ["derive"] }
serde_json = "1.0"

...


use actix_web::{ResponseError, HttpResponse};
use thiserror::Error;
use serde_json::json;

#[derive(Debug, Error)]
pub enum ApiError {
    #[error("Invalid email format")]
    InvalidEmail,

    #[error("Missing required field: {0}")]
    MissingField(String),
}

...


/// To convert the error into an HTTP response, we implement the ResponseError trait. The error_response method defines how Actix should handle the error when it is returned in a route handler. The "ResponseError" trait with the "error_response" method is automatically detected for actix-web and will use it automatically on elements that implement this trait
/// Actix-web automatically detects and calls the error_response() method from the ResponseError trait when an error is returned from a route handler.
/// When you return Err(ApiError::InvalidEmail), Actix-web automatically converts it into an HTTP response by calling the error_response() method you defined in the ResponseError implementation. */
/// This behavior is expected and built into Actix-web for error handling.
impl ResponseError for ApiError {
    fn error_response(&self) -> HttpResponse {
        match *self {
            ApiError::InvalidEmail => {
                HttpResponse::BadRequest().json(json!({ "error": "Invalid email format" }))
            }
            ApiError::MissingField(ref field) => {
                HttpResponse::BadRequest().json(json!({ "error": format!("Missing field: {}", field) }))
            }
        }
    }
}

...

#[derive(serde::Deserialize)]
struct UserInput {
    email: String,
}


fn validate_input(input: &UserInput) -> Result<(), ApiError> {
    if input.email.trim().is_empty() {
        return Err(ApiError::MissingField("email".to_string()));
    }
    if !input.email.contains('@') {
        return Err(ApiError::InvalidEmail);
    }
    Ok(())
}

async fn create_user(input: web::Json<UserInput>) -> Result<HttpResponse, ApiError> {
    /// Using `?` to propagate errors
    /// If this fails, the function returns early with the error; if no fail occurs, it just goes on
    /// This is basically the cleaner alternative for a "match" statement where you would check for "Err" or "Ok" and return early if an "Err" is detected
    validate_input(&input)?;
    Ok(HttpResponse::Ok().json(json!({ "message": "User created successfully" })))
}
```

There are more actix-web traits which are automatically used to simplify response generation, extracting data, and middleware handling:

- [Responder](https://docs.rs/actix-web/latest/actix_web/trait.Responder.html) - Automatically converts return values into HTTP responses.
- [FromRequest](https://docs.rs/actix-web/latest/actix_web/trait.FromRequest.html) - Automatically extracts request data into handler parameters.
- [ResponseError](https://mozilla-services.github.io/merino/rustdoc/actix_web/error/trait.ResponseError.html) - see example above
- https://docs.rs/actix-web/latest/actix_web/index.html#traits

### Creating custom declarative macros

To make custom macros available in other files, you have to export them:

```rs
#[macro_export]

macro_rules! my_macro {...}
```

When creating a custom macro, you have to use macro captures:

- item: Captures any Rust item, such as functions, structs, enums, traits, impl blocks, etc.
- block: Captures a code block (enclosed in {}).
- stmt: Captures a statement, which can be followed by ; or =>.
- pat: Captures a pattern, typically used in match arms or function parameters.
- expr: Captures an expression, such as a + b or function calls.
- ty: Captures a type, including paths, generics, and type casts.
- ident: Captures an identifier (a variable, function, or type name).
- path: Captures a path (like std::collections::HashMap).
- meta: Captures meta attributes used in #[...] annotations.
- tt: Captures a single token tree (any valid Rust syntax unit).

```rs
macro_rules! custom_macro {
  ($x: ty) => {
    match stringify!($x) {
    "i32" => "You sent an i32 type".to_string(),
    _ => "You sent something else".to_string(),
    }
  }
}
```

Another example (from codingame):

```rs
macro_rules! parse_input {
    ($x:expr, $t:ident) => ($x.trim().parse::<$t>().unwrap())
}
```

You may also make use of repetition specifiers:

- `*` match zero or more repetitions
- `+` match one or more repetitions
- `?` match zero or one repetition

```rs
// Basically like vec!() but it requires to provided at least one argument
macro_rules! my_vec {
  ($($x: expr), +) => {
    {
      // Create the vector
      let mut temp_vec = Vec::new();

      // Push one or more elements (given through $x) to the vector
      // Using it like "$(...)+" basically serves as a loop for all the values from $x (repetition block)
     $(
      temp_vec.push($x);
      )+

      // Return the vector
      temp_vec
    }
  }
}
```

Those were just declarative macros, there are also [procedural macros](https://www.udemy.com/course/autogpt-gpt4-code-writing-ai/learn/lecture/38205574#overview) which get way more advanced.

#### custom hashmap! declarative macro

This creates a declarative hashmap! macro which can be used to shorthand create a hashmap with initial values

```rs
use std::collections::HashMap;

macro_rules! hashmap_with_tuple {
    ($(($key: expr, $value: expr)), +) => {{
        let mut map: HashMap<_, _> = HashMap::new();

        $( map.insert($key, $value); )+

        map
        }
    };
}

macro_rules! hashmap_with_token_tree_syntax {
    ($($key: expr => $value: expr), +) => {{
        let mut map: HashMap<_, _> = HashMap::new();

        $( map.insert($key, $value); )+

        map
        }
    };
}

fn main() {
    let hashmap_with_tuple_test = hashmap_with_tuple!((1, "one"), (2, "two"));
    let hashmap_with_token_tree_syntax_test =
        hashmap_with_token_tree_syntax!(1 => "one", 2 => "two");

    dbg!(hashmap_with_tuple_test);
    dbg!(hashmap_with_token_tree_syntax_test);
}
```

### Async API Call with tokio, reqwest, and serde_json

The `?` operator activates the functionality that in case of an error the whole function would throw an error like `Err(...)` instead of having the application panic (when using `unwrap()`, for example).

`serde_json` will automatically parse the data fetched from the API in proper types which can be used by Rust.
Thus, having like a string, would be fetched as `String(...)`.

```rs
async fn async_call(url: &str) -> Result<serde_json::Value, reqwest::Error> {
  let response: serde_json::Value = reqwest::get(url)
    .await?
    .json::<serde_json::Value>()
    .await?;

  Ok(response)
}



#[cfg(test)]
mod tests {
  use super::*

  #[tokio::test]
  async fn tests_async_call_fn() {
    let api_url: &str = "...";
    let my_res = async_call(api_url).await;

    match my_res {
      Ok(res) => {
        dbg!(res)
      },
      Err(_) => {
        panic!("Failed!")
      }
    };
  }
}
```

You could also have handled the errors like this (for cases with alternative error types):

```rs

...

let response = reqwest::get(url)
  .await
  .map_err(|_| std::io::Error::new(std::io::ErrorKind::Other, "Could not retrieve response"))?;

let json_response: serde_json::Value = response
  .json::<serde_json::Value>()
  .await
  .map_error(|_| std::io::Error::new(std::io::ErrorKind::Other, "Could not decode to JSON"))?;
```

You could also have used `expect()`, `expect_err()`, or even `unwrap()` etc.

### Number Literals

```rs
println!("Big number is {}", 98_222_000);
println!("Hex is {}", 0xff);
println!("Octal is {}", 0o77);
println!("Binary is {}", 0b1111_0000);
println!("Bytes 'A' is {}", b'A');
```

### Raw - String Literal

```rs
let text: &str = r#"{"message": "Rust is awesome"}"#
```

### Writing a Unit Test

```rs
pub fn add_five(num: u32) -> {
    num + 5
}

#[cfg(test)]
mod test {
    use super::*

    #[test]
    fn adds_five_test() {
        let x: u32 = 100;
        let y: u32 = add_five(x);

        println!("x and y are from test: {} {}", x, y);

        assert_eq!(y, 105);
    }
}
```

### Import Modules

```
├── main.rs (in here, use 'mod funcs_a' and 'mod other_funcs' (the folder's name), then you can access the crates like 'use crate::other_funcs::some_function)
├── funcs_a.rs (have your functions in here)
│   ├── other_funcs\
│   |   ├── funcs_b.rs (have your functions in here)
│   |   ├── mod.rs (in here, use 'pub mod funcs_b')
```

### Read txt file input (two values on each line with space character between)

```rs
use std::fs::File;
use std::io::{self, BufRead};

...

let path = "src/values.txt";

let mut left_column = Vec::new();
let mut right_column = Vec::new();

let file = File::open(&path)?;
let reader = io::BufReader::new(file);

for line in reader.lines() {
    let line = line?;
    let parts: Vec<&str> = line.split_ascii_whitespace().collect();

    if parts.len() == 2 {
        if let (Ok(left), Ok(right)) = (parts[0].parse::<i32>(), parts[1].parse::<i32>()) {
            left_column.push(left);
            right_column.push(right);
        }
    }
}
```

### Move Keyword in a Closure

The `move` keyword is used to transfer ownership of variables to a closure when capturing them.

```rs
fn main () {
    let mut print;

    {
        let mut x = 10;

        print move || { // Without the `move` keyword, x would not live long enough since it's dropped at the end of this current scope while it's still used within the print function outside of the scope afterwards
            x += 1;
            println!("Modified x: {}", x);
        }
    }

    print();
}

```

### Value Consuming Closure

```rs
fn main () {
    let mut x = "10".to_string();

    let print = || {
        x += "11";
        println!("Modified x: {}", x);
        x
    }

    println!("{}", print());
    // print() cannot be called another time since the variable x was consumed/moved outside of the current environment in the first print() call (FnOnce trait)
}

```

### Enum

Instead of having three different classes in JavaScript for Rectangle, Circle, and Triangle, in Rust you can use one Enum which implementes corresponding methods for each case.

```rs
#[derive(Debug)]
enum Shape {
    Rectangle { width: f64, height: f64 },
    Circle { radius: f64 },
    Triangle { base: f64, height: f64 },
}

impl Shape {
    // Method to calculate the area of the shape
    fn area(&self) -> f64 {
        match self {
            Shape::Rectangle { width, height } => width * height,
            Shape::Circle { radius } => std::f64::consts::PI * radius.powi(2),
            Shape::Triangle { base, height } => 0.5 * base * height,
        }
    }

    // Method to describe the shape
    fn describe(&self) -> String {
        match self {
            Shape::Rectangle { width, height } => {
                format!("Rectangle with width {} and height {}", width, height)
            }
            Shape::Circle { radius } => format!("Circle with radius {}", radius),
            Shape::Triangle { base, height } => {
                format!("Triangle with base {} and height {}", base, height)
            }
        }
    }
}

fn main() {
    let rect = Shape::Rectangle { width: 10.0, height: 5.0 };
    let circ = Shape::Circle { radius: 3.0 };
    let tri = Shape::Triangle { base: 4.0, height: 6.0 };

    println!("{} has an area of {:.2}", rect.describe(), rect.area());
    println!("{} has an area of {:.2}", circ.describe(), circ.area());
    println!("{} has an area of {:.2}", tri.describe(), tri.area());
}
```

### Trait Bounds

**only those types with all needed traits are accepted for this function's calls:**

```rs
fn some_function<T>(v: &v[T]) -> Option<T>
    where T: std::cmp::PartialOrd + Copy // This is the Trait Bound
{
    ...
}
```

**Same procedure for methods of a Struct:**

```rs
struct Rectangle<T> {
    width: T,
    height: T,
}

// This uses the default syntax for applying a trait bound (without the `where` operator)
impl<T: std::ops::Mul<Output = T> + Copy> Rectangle<T> {
    fn area(&self) -> T {
        self.width * self.height
    }
}
```

### Pass an Immutable Value to a Function that Handles it as Mutable Inside

```rs
fn increment(mut x: i32) -> i32 {
    x += 1; // Modify x inside the function
    x       // Return the modified value
}

fn main() {
    let num = 5;          // num is immutable in main
    let new_num = increment(num); // Pass num by value (a copy is made)
    println!("{}", num);      // Output: 5 (original value is unchanged)
    println!("{}", new_num);  // Output: 6 (returned value)
}
```

**Useful when:**

- You want to work with a mutable copy of the value without affecting the original.
- You don’t want to require mutability in the caller: The caller can pass an immutable variable (let num = 5), and the function still works, because the function creates its own mutable copy of the value.

**But:**

- The behavior described above works because i32 implements the Copy trait.
  For non-Copy types like String, passing a value to the function would involve an ownership transfer, and the original value would no longer be accessible in the caller.

**Example for non-Copy types:**

```rs
fn modify(mut s: String) -> String {
    s.push_str(" world");
    s
}

fn main() {
    let text = String::from("Hello");
    let new_text = modify(text); // Ownership of `text` is moved
    // println!("{}", text); // ERROR: text is no longer accessible
    println!("{}", new_text); // Output: Hello world
}
```

### Create a Custom Trait, Implement It And Create a Function With a Corresponding Trait Object (Including Associated Type, Display Trait Implementation)

```rs
use std::fmt; // Used for the Display Implementation


trait Animal {
    fn make_sound(&self);
    type Weight; // This is an Associated Type
    fn set_weight(&mut self, weight: Self::Weight);
    fn get_weight(&self) -> Self::Weight;
    fn set_age(&mut self, _age: u8) {
        println!("This feature is not suppored!"); // This is used as the default function's implementation
    }
    fn get_age(&self) -> u8 {
        println!("This feature is not suppored!"); // This is used as the default function's implementation
        0
    }
}

struct Dog {
    age: u8;
    weight: u8;
}

// This implements the Display trait that can't be automatically derived (used to make println!("{}", instance_of_dog) work)
impl fmt::Display for Dog {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        if let Some(w) = f.width() { // This is used to have the option to provide a width like println!("{:15}", instance_of_dog) for the displaying
            writeln!(f, "{:#^w$}", " Dog Details ", w = 2 * w)?;
            writeln!(f, "{:<w$}:{:>w$}", "Age", self.age)?;
            writeln!(f, "{:<w$}:{:>w$}", "Weight", self.weight)?;
            writeln!(f, "{:<w$}:{:>w$}", "Name", self.name)?;
        } else {
            writeln!(f, "{:#^17}", " Dog Details ")?;
            writeln!(f, "{:<8}:{:>8}", "Age", self.age)?;
            writeln!(f, "{:<8}:{:>8}", "Weight", self.weight)?;
            writeln!(f, "{:<8}:{:>8}", "Name", self.name)?;
        }

        Ok(())
    }
}


// This implements the Animal trait for the Dog struct with all methods defined
impl Animal for Dog {
    fn make_sound(&self) {
        println!("bark!");
    }

    type Weight = u8;

    fn set_weight(&mut self, weight: u8) {
        self.weight = weight; // Rust dereferences &mut self automatically to get to the actual struct
    }

    fn get_weight(&self) -> u8 {
        self.weight
    }

    fn set_age(&mut self, age: u8) {
        self.age = age;
    }

    fn get_age(&self) {
        self.age
    }
}

struct Cat {
    age: u8;
    weight: f32;
}

// This implements the Animal trait for the Cat struct but two methods are not defined and will use the default implementation from the trait
impl Animal for Cat {
    fn make_sound(&self) {
        println!("meow!");
    }

    type Weight = f32;

     fn set_weight(&mut self, weight: f32) {
        self.weight = weight;
    }

    fn get_weight(&self) -> f32 {
        self.weight
    }
}

// This function can be used for any struct that implements the Animal trait.
// The `&dyn Animal` type is a trait object, which allows for dynamic dispatch.
// This means that at runtime, the actual type of the object (any type implementing the Animal trait)
// will be determined, and the appropriate implementation of `make_sound` will be called.
// Weight = T is needed due to the added implemented associated type to the trait
fn produce_sound<T>(animal: &dyn Animal<Weight = T>) {
    animal.make_sound();
}
```

### Initialize a Struct Instance with Default Values

```rs
struct Person {
    name: String,
    age: u8,
    height: f32,
}

let user = Person::default() // Use this for adding default values for all fields of this instance

// Use this approach to assign some fields to specific values and default values for all the other fields of that instance
let user_2 = Person {
    name: "Ally".to_string(),
    ..Default::default()
};
```

You may also use the `Default` trait like this instead of calling the `default()` function:

```rs
#[derive(Default)]
struct Person {
    name: String,
    age: u8,
    height: f32,
}
```

### Counting Digits in String

```rs
fn nb_dig(n: i32, d: i32) -> i32 {
    let ex = d.to_string();
    (0..=n).map(|v| (v*v).to_string()).fold(0, |acc, v| acc + v.matches(&ex).count() as i32)
}
```

### Odd or Even Sum

```rs
fn odd_or_even(numbers: Vec<i32>) -> String {
    match numbers.iter().sum::<i32>() % 2 == 0 {
        true => "even".to_string(),
        false => "odd".to_string()
    }
}
```

### Get First Char and Return String

```rs
fn are_you_playing_banjo(name: &str) -> String {
    let first_char = name.chars().next().unwrap();

    if first_char == 'r' || first_char == 'R' {
        return format!("{} plays banjo", name)
    }

    format!("{} does not play banjo", name)
}
```

### String Transformation

```rs
fn accum(s: &str) -> String {
    s.chars()
        .enumerate()
        .map(|(i, c)| {
            let mut result = String::new();
            result.push(c.to_ascii_uppercase());
            result.push_str(&c.to_ascii_lowercase().to_string().repeat(i));
            result
        })
        .collect::<Vec<String>>()
        .join("-")
}

fn main() {
    let result = accum("abcd");
    println!("{}", result);  // Output: "A-Bb-Ccc-Dddd"
}
```

### IsPrime

```rs
fn isPrime(n: i32) -> bool {
    let mut i = 2;

    while i * i <= n {
        if n % i == 0 {
            return false;
        }

        i += 1;
    }

    return n > 1;
}
```

### Next Char in Alphabet with Wrap-Around

```rs
fn main() {
    let mut input_line = String::new();
    io::stdin().read_line(&mut input_line).unwrap();
    let letter = input_line.trim().to_string();

    // This is basically charCodeAt()
    let char_code = letter.chars().next().unwrap() as u32 + 1;

    // Wraps around the alphabet if the new char code would exceed the threshold of the lowercase alphabet characters
    let new_char_code = 97 + (char_code - 97) % 26;
    let new_char = char::from_u32(new_char_code).unwrap();

    // This is the method for String.fromCharCode()
    println!("{}", std::char::from_u32(new_char_code).unwrap())
}
```

### Find Temperature closest to 0

```rs
...
    let mut numbers_iter = inputs.split_whitespace();

    if numbers_iter.clone().count() == 0 {
        println!("{}", 0);
        return;
    }

    let mut ans: i32 = numbers_iter.next().unwrap().parse::<i32>().unwrap();

    for i in inputs.split_whitespace() {
        let t = parse_input!(i, i32);

        if t.abs().cmp(&ans.abs()) == Ordering::Less || (t.abs() == ans.abs() && t > ans) {
            ans = t;
        }
    }
...
```

### Let Some & Unicode Transform

```rs
    if let Some(unicode_char) = char::from_u32(n as u32) {
        if unicode_char.is_digit(10) {
            let ans = n / unicode_char.to_digit(10).unwrap() as i32;
            println!("{}", ans);
        } else {
            println!("ERROR!");
        }
    } else {
        println!("Parsing Error");
    }
```

### Shortened CodinGame example

```rs
use std::io;

macro_rules! parse_input {
    ($t:ident) => {
        {
            let mut input_line = String::new();
            io::stdin().read_line(&mut input_line).unwrap();
            input_line.trim().parse::<$t>().unwrap()
        }
    };
}

fn main() {
    println!("{}", (parse_input!(f64) / (1.0 - (parse_input!(f64).log10() - parse_input!(f64).log10()))) as i32);
}
```

### Convert Number to Binary and Back

```rs
    let number = 42;
    let binary_string = format!("{:b}", number);

    // Convert binary back to number
    let binary_number = u32::from_str_radix(&binary_string, 2).unwrap();
```

### Create HashSet with Initial Values

```rs
 let technologies: HashSet<String> = ["HTML", "CSS", "JavaScript", "Bootstrap", "Tailwind CSS", "React", "Vue.js", "Angular"]
        .iter()
        .cloned()
        .map(String::from)
        .collect();
```

### Create HashMap with Initial Values

```rs
let technologies: HashMap<&str, &str> = [
        ("HTML", "Markup language for creating web pages"),
        ("CSS", "Style sheet language for designing web pages"),
    ].iter().cloned().collect();
```

### Count Word Occurences in a String and Print Them in Their Order of Appearance

```rs
fn main() {
    let mut input_line = String::new();
    io::stdin().read_line(&mut input_line).unwrap();
    let message = input_line.trim_matches('\n').to_string();
    let mut words: HashMap<&str, i32> = HashMap::new();
    let mut order: Vec<&str> = Vec::new();

    for word in message.split_ascii_whitespace() {
        if !words.contains_key(word) {
            order.push(word);
        }

        *words.entry(word).or_insert(0) += 1;
    }

    for word in order {
        if let Some(count) = words.get(word) {
            println!("{}: {}", word, count);
        }
    }
}
```

### Change the First Letter of a String

```rs
let mut chars = val.chars().collect::<Vec<char>>();

if let Some(first_char) = chars.get_mut(0) {
    *first_char = first_char.to_ascii_uppercase();
}

ans.push(chars.into_iter().collect::<String>());
```

### Check for Missing Socks and Sort Them by Size, Then Color

```rs
use std::io;
use std::collections::HashMap;
use itertools::Itertools;

macro_rules! parse_input {
    ($x:expr, $t:ident) => ($x.trim().parse::<$t>().unwrap())
}

fn main() {
    let mut input_line = String::new();
    io::stdin().read_line(&mut input_line).unwrap();
    let n = parse_input!(input_line, i32);
    let mut socks: HashMap<String, i32> = HashMap::new();

    for _ in 0..n as usize {
        let mut input_line = String::new();
        io::stdin().read_line(&mut input_line).unwrap();
        let inputs = input_line.split(" ").collect::<Vec<_>>();
        let clothes_type = inputs[0].trim().to_string();
        let clothes_size = parse_input!(inputs[1], i32);
        let clothes_color = inputs[2].trim().to_string();

        if clothes_type == "sock" {
            let cur = format!("{} {}", clothes_size, clothes_color);

            *socks.entry(cur).or_insert(0) += 1;
        }
    }

    let mut filtered: Vec<(&String, &i32)> = socks.iter().filter(|(_, &v)| v % 2 != 0).collect();
    println!("{}", filtered.len());

    filtered.sort_by(|a, b| {
        let (a_size, a_color) = parse_key(a.0);
        let (b_size, b_color) = parse_key(b.0);

        a_size.cmp(&b_size).then(a_color.cmp(&b_color))
    });

    for (key, _) in filtered.iter() {
        println!("{}", key);
    }
}

fn parse_key(key: &str) -> (i32, &str) {
    let parts: Vec<&str> = key.split_whitespace().collect();
    let number = parts[0].parse::<i32>().unwrap();
    let color = parts[1];
    (number, color)
}
```

### Multi-Task Multi-Thread Approach for Incoming Request With Tokio Crate

```rs
use tokio::time::{sleep, Duration};

#[tokio::main]
async fn main() {
    let max_concurrent_tasks = 10;
    let sem = tokio::sync::Semaphore::new(max_concurrent_tasks); // Limits to 10 concurrent tasks


    let tasks: Vec<_> = (0..15) // Simulate 15 incoming requests
        .map(|i| {
            let permit = sem.clone().acquire_owned();
            tokio::spawn(async move {
                let _permit = permit.await.unwrap();
                handle_request(i).await;
            })
        })
        .collect();

    for task in tasks {
        task.await.unwrap();
    }

    println!("All requests handled.");
}

async fn handle_request(id: usize) {
    println!("Handling request: {}", id);
    sleep(Duration::from_secs(2)).await;
    println!("Completed request: {}", id);
}
```

- **Out-of-Order Completion**: Since tasks are concurrent, some may take longer than others, leading to a completion order that doesn’t necessarily match the order in which requests were received.

**Semaphore (tokio::sync::Semaphore):**

- The Semaphore::new(max_concurrent_tasks) limits the number of concurrent tasks that can run at the same time. In your case, it's set to max_concurrent_tasks = 10, so no more than 10 tasks can run concurrently.
- Each task acquires a permit from the semaphore before it can start. When a task finishes (or awaits something like sleep), it releases the permit, allowing another task to acquire it and run.

**Task Execution:**

- tokio::spawn schedules the tasks to run asynchronously, but the tasks don't necessarily run on different threads at once. Instead, the tasks are executed on a limited number of threads from the Tokio runtime's thread pool.
- Tokio uses a single or small number of threads (depending on the runtime configuration) to handle many tasks. So, it may start with 10 tasks running concurrently (on separate threads or on the same thread, depending on how the runtime schedules them).
- When a task hits await, such as sleep(Duration::from_secs(2)).await;, it yields the thread back to the runtime (meaning, it does not occupy the thread anymore) so that another task can run in the meantime, even though the task is not finished. The same thread can then be reused by other tasks.

**What's Happening When a Task Hits await?**
When a task calls .await, it’s pausing its execution until the awaited operation (like sleep(Duration::from_secs(2))) is finished. Here's the important part:

- Task Context Switch: When a task is awaiting, it does not block the thread it is running on. Instead, the task is suspended and the thread becomes available to run other tasks.
- Thread Pool: Even though all tasks are managed within the runtime, multiple tasks may be scheduled to run on a pool of threads. If a task is paused while awaiting, the runtime can execute another task on that same thread.
- No "Blocking": The thread isn't being "held up" or "blocked" by the awaiting task, which is the key idea. The thread is available to process other tasks that are ready to run. This is very different from traditional multi-threading, where tasks block their threads while waiting.

**Concurrency, Not Parallelism:**

- While tasks are running concurrently, they are not running in parallel unless the runtime is configured with multiple threads and multiple tasks need to be executed simultaneously.
- The key concept here is that while tasks are waiting (e.g., on await), the runtime will switch between tasks, allowing other tasks to proceed without blocking. This is how I/O-bound tasks (like waiting for a web request) can be efficient, as they don't block the whole system.
- The tasks will share threads and only use new threads as necessary, allowing concurrency without requiring a large number of OS threads.

### Change Value of an Array

```rs
let mut numbers = [23, 34, 5, 6, 7, 88];

for n in &mut numbers {
    if *n < 10 {
        *n = 0;
    }
}
```

**Alternative Approach:**

```rs
let mut numbers = [23, 34, 5, 6, 7, 88];

for i in 0..numbers.len() {
    if numbers[i] < 10 {
        numbers[i] = 0;
    }
}
```

Result of numbers array would be [23, 34, 0, 0, 0, 88] in both cases.

### While Let Loop

Similar to `if let`, using a pattern match (normally used for de-structuring an `Option` (`Some` and `None`) or `Result` (`Ok` and `Err`))

```rs
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let mut iterator = numbers.iter();

while let Some(number) = iterator.next() {
    ...
}
```

### 'outer and 'inner Loops

You can name 'outer and 'inner anything you like.

```rs
let result = 'outer: loop {
    for i in 1..5 {
        println!("Outer loop iteration: {}", i);
        'inner: for j in 1..5 {
            println!("  Inner loop iteration: {}", j);
            if i * j == 6 {
                break 'outer "Match found at i * j = 6"; // Exit both loops and return a string
            } else if i + j == 3 {
                break 'inner; // Exit the inner loop only and continue with the next iteration of the outer loop
            }
        }
    }
    break "No match found"; // This will be executed if no condition in the inner loop matches
};
```

## Project Structuring

- **Binary Crate (`main.rs`):** This is defined by having a `main.rs` file, which is the entry point for a binary executable. The `main.rs` file is responsible for running the actual application and can utilize the library crate by importing its modules.

- **Library Crate (`lib.rs`)**: This is defined by having a `lib.rs` file which acts as the root of the library. It's used to compile code that is meant to be reused by other Rust projects or binaries within the same project.

The project may include subdirectories like this:

```
src/
├── lib.rs         # Root file of the library crate
├── main.rs        # Root file of the binary crate
└── utils/
    ├── mod.rs     # Makes utils a submodule of the library, declared in lib.rs
    └── calculations.rs
```

Here, the modules from `calculations.rs` would be defined in the `utils/mod.rs` (like `pub mod calculations`), to make the modules accesible from elsewhere. Then, you would also have to use `pub mod utils` in the `lib.rs` file to make the whole utils modules' directory accessible from anywhere (other packages that use your package as dependency).

## Lifetimes

**Example Code:**

```rs
#[derive(Insertable)]
#[table_name = "users"]
struct NewUser<'a> {
    name: &'a str,
    email: &'a str,
}

fn create_user<'a>(name: &'a str, email: &'a str) -> NewUser<'a> {
    NewUser { name, email }
}

fn main() {
    let name = "Alice";    // This string slice has an implicit lifetime
    let email = "alice@example.com";

    let user = create_user(name, email);  // No need to specify lifetimes explicitly
    println!("User: {}, Email: {}", user.name, user.email);
}
```

In this context, <'a> is a lifetime annotation in Rust. Lifetimes are a way of telling the Rust compiler how long references should be valid to prevent dangling references or invalid memory access. In the example you've given, <'a> specifies that the references (&'a str) inside the NewUser struct must live at least as long as the lifetime 'a.

**Here’s what it means step by step:**

- Explanation of <'a>:
  'a is a lifetime: The <'a> after the struct name indicates that the struct has a generic lifetime parameter 'a. This lifetime is a placeholder representing the scope during which the data referenced by name and email will be valid.

- &'a str: Both the name and email fields are references to str slices, and these references are annotated with the lifetime 'a. This means that these references must point to data that will live for at least as long as 'a.

- Lifetime ensures data validity: By specifying the lifetime 'a, Rust guarantees that the data being referenced (in name and email) will not be invalidated (dropped) while the NewUser struct is still being used. In other words, the struct can’t outlive the data it references.

To invoke a function with lifetime annotation, you don't need to explicitly provide the lifetime 'a in the function call. Rust's compiler automatically infers lifetimes based on the input and output references. Here's how you would call the function:

- String literals like "Alice" and "alice@example.com" are static, meaning they have the 'static lifetime, which means they are valid for the entire program.
- The create_user function accepts &'a str (references with some lifetime 'a), and Rust automatically infers the lifetime 'a for these inputs.
- You just call the function by passing string slices (or any other references that fit the lifetime constraints). Rust figures out the correct lifetimes and ensures everything is safe.

You don’t need to explicitly specify lifetimes when invoking the function, because lifetimes are part of Rust’s type system, but the actual annotation is only required in function or struct definitions. When calling a function, Rust’s compiler infers the correct lifetimes based on the references you pass.

## Ownership

Ownership is a set of rules that govern how a Rust program manages memory.

- Each value in Rust has an owner.
- There can only be one owner at a time.
- When the owner goes out of scope, the value will be dropped.

## The Stack and the Heap

Both the stack and the heap are parts of memory available to your code to use at runtime, but they are structured in different ways. The stack stores values in the order it gets them and removes the values in the opposite order. This is referred to as last in, first out. Think of a stack of plates: when you add more plates, you put them on top of the pile, and when you need a plate, you take one off the top. Adding or removing plates from the middle or bottom wouldn’t work as well! Adding data is called pushing onto the stack, and removing data is called popping off the stack. All data stored on the stack must have a known, fixed size. Data with an unknown size at compile time or a size that might change must be stored on the heap instead.

The heap is less organized: when you put data on the heap, you request a certain amount of space. The memory allocator finds an empty spot in the heap that is big enough, marks it as being in use, and returns a pointer, which is the address of that location. This process is called allocating on the heap and is sometimes abbreviated as just allocating (pushing values onto the stack is not considered allocating). Because the pointer to the heap is a known, fixed size, you can store the pointer on the stack, but when you want the actual data, you must follow the pointer. Think of being seated at a restaurant. When you enter, you state the number of people in your group, and the host finds an empty table that fits everyone and leads you there. If someone in your group comes late, they can ask where you’ve been seated to find you.

The heap is used for dynamic memory allocation, where the size of the data might not be known at compile time or can change at runtime. Complex types such as String, vectors (Vec<T>), and other types that can grow or shrink at runtime are stored on the heap. When you use such types in Rust, what's actually stored on the stack is a pointer (or multiple pointers) to the data on the heap. This pointer contains the memory address of the actual data.

Pushing to the stack is faster than allocating on the heap because the allocator never has to search for a place to store new data; that location is always at the top of the stack. Comparatively, allocating space on the heap requires more work because the allocator must first find a big enough space to hold the data and then perform bookkeeping to prepare for the next allocation.

Accessing data in the heap is slower than accessing data on the stack because you have to follow a pointer to get there. Contemporary processors are faster if they jump around less in memory. Continuing the analogy, consider a server at a restaurant taking orders from many tables. It’s most efficient to get all the orders at one table before moving on to the next table. Taking an order from table A, then an order from table B, then one from A again, and then one from B again would be a much slower process. By the same token, a processor can do its job better if it works on data that’s close to other data (as it is on the stack) rather than farther away (as it can be on the heap).

When your code calls a function, the values passed into the function (including, potentially, pointers to data on the heap) and the function’s local variables get pushed onto the stack. When the function is over, those values get popped off the stack.

Keeping track of what parts of code are using what data on the heap, minimizing the amount of duplicate data on the heap, and cleaning up unused data on the heap so you don’t run out of space are all problems that ownership addresses. Once you understand ownership, you won’t need to think about the stack and the heap very often, but knowing that the main purpose of ownership is to manage heap data can help explain why it works the way it does.

Besides the Stack and the Heap, there is also the Static Memory (RODATA), for example. References to string literals (&str) or other constant data are stored in static (read-only) memory.

```rs
let s: &str = "hello";  // Stored in RODATA, s is a reference to it
```

### Example

Consider a String type in Rust. When you create a String, the struct that represents the String (which includes the pointer, length, and capacity) is stored on the stack. The actual contents of the string, however, are stored on the heap. The pointer in the String struct points to this heap-allocated memory where the characters of the string are stored.

```js
let s = String::from("hello");
```

In this example, s is a variable on the stack that contains a String struct. This struct contains a pointer to the heap where the actual "hello" string is stored. The String struct itself might contain more than just a pointer (like length and capacity), but the crucial part for this discussion is that the character data is on the heap, and s on the stack points to it.

### Alternative Explanation

In both C++ and Rust, memory is divided into two main regions: the stack and the heap.

**Stack**:

- This is where static or local variables (like function arguments and local variables) are stored.
- The stack is fast and has automatic memory management (when a function returns, its local variables are popped off the stack).
- Memory allocated on the stack is of fixed size and is known at compile time.
- Data like integers, floats, and small structs/enums are often allocated here.

**Heap**:

- The heap is for dynamically allocated memory. This is useful when you need to allocate large or variable-sized data at runtime.
- It’s slower because you have to explicitly manage memory (allocate and deallocate).
- Data structures like vectors, boxes, or any large complex structures that you allocate at runtime are typically stored here.

A pointer is a variable that holds the address of a memory location. This memory can be on the stack or heap.
In both C++ and Rust, pointers allow you to reference data from either memory region, but they work a bit differently in each language.

**In C++**:

- You have raw pointers (int\* ptr), which directly reference a memory address. However, managing the lifecycle of heap-allocated memory (like new and delete) is manual, which can lead to memory leaks, dangling pointers, or null pointers.

- If the pointer is no longer valid (because you freed or modified the memory it points to), dereferencing it can cause undefined behavior, including null pointer dereferencing or accessing garbage data.

**In Rust**:

- You have more safe abstractions over pointers. Rust uses references (&T) and smart pointers like Box, Rc, and Arc, which manage memory more safely.

- Rust's ownership and borrowing system prevents many pointer-related issues by enforcing strict rules at compile time (like preventing dangling pointers). Ownership means who is responsible for cleaning up (dropping) a value. When you have a variable like let x = 5;, x owns that value. &mut is a mutable reference, a temporary borrow of the owner’s value. It does not own the data; it just has permission to modify it while the borrow lasts. The owner still exists somewhere, and Rust enforces that:
  - There is exactly one mutable reference (&mut) OR
  - Any number of immutable references (&)
  - But never both at the same time.

- Null pointers are largely avoided in Rust because Rust doesn’t allow null references. Instead, you use the Option<T> type, where None can represent the absence of a value, avoiding the risk of null pointer dereferencing.

**Heap-allocated data in both C++ and Rust typically involves**:

- Dynamically sized collections (like arrays, vectors, linked lists).
- Large data structures whose size cannot be known at compile time.

A null pointer occurs when a pointer is explicitly set to a null value (nullptr in C++ or Option::None in Rust).
Dangling pointers or use-after-free errors. These occur when:

- A pointer/reference points to memory that has been freed (invalid memory), but the pointer still "thinks" it is valid.
  For example, if you free a heap-allocated object and try to access it via the pointer, this leads to undefined behavior.
- Rust prevents these issues with its ownership model: when a value is deallocated, all references to it are automatically invalidated by the compiler, making dangling pointers impossible unless you opt into unsafe code.

## `struct`

In Rust, a struct (short for "structure") is a custom data type that lets you name and package together multiple related values that make up a meaningful group. It's similar to a record, struct in C, or a class in other object-oriented languages (without the methods). Structs are a fundamental concept in Rust, used to create custom types.

## The `&` Symbol in Rust

The following information is based on this example:

```rust
use ferris_says::say;
use std::io::{stdout, BufWriter};

fn main() {
    let message: String = String::from("Hello fellow Rustaceans!");
    let width: usize = message.chars().count();

    let mut writer = BufWriter::new(stdout());
    say(&message, width, &mut writer).unwrap();
}
```

The `&` symbol is used for referencing in Rust. It creates a reference to a value without taking ownership of it. In Rust, every value has a single owner, and when the owner goes out of scope, the value is dropped. References allow you to refer to a value without owning it.

In the context of `&message`: Here, `&message` creates a reference to the `message` variable. The say function doesn't take ownership of `message`; it only needs to read the data. By passing a reference, you allow say to use `message` without taking ownership, so `message` can be used later in your function if needed.

In the context of `&mut`: When you see `&mut`, it signifies a mutable reference. This means that not only is the function referencing the variable, but it also needs to modify it. Mutable references allow you to change the data the reference points to. In `&mut` writer, it indicates that the say function might modify the writer.

**Also:**
The & symbol in Rust can serve different roles depending on the context, and understanding these can clarify how Rust handles references and dereferencing:

1. Creating References: In the context of creating references, & is used to borrow a value, creating a reference to it. For example, let ref_to_x = &x; creates a reference ref_to_x that points to the value of x.

2. Pattern Matching/Destructuring: When used in the context of a pattern (like in function arguments, let bindings, or match arms), & can actually perform a dereference operation.
   For example, in a function call like function(&x), &x is passing a reference to x. However, in the function signature, if you see something like fn function(&x: &i32), the & in &x is actually dereferencing the passed reference to directly work with the value in the function body, without needing to manually dereference it using \*.

### Pattern Matching

The following explanation is based on this code example:

```rs
    let my_array = [1, 2, 3, 4, 5];
    let slice = &my_array[..];

    for i in slice {
        println!("{}", i)
    }
```

When you write `for i in slice` here, i is a reference to the element of the array,
so it has the type &i32 because the array slice `&my_array[..]` is a reference to the array elements.

When you would use `for &i in slice`, pattern matching would be utilized.
In such a case, the &i pattern means that you are destructuring the reference &i32 into the value it points to, which is of type i32.
So, instead of getting a reference to each element (&i32), you pattern match to extract the value (i32).
The reason it doesn't become &&i32 is that pattern matching with &i destructures one level of reference, converting &i32 into i32.

**Another Example for Pattern Matching**

```rs
fn main() {
    let value = Some(42);
    match &value {
        Some(&x) => println!("Matched x = {}", x), // x is a plain value
        None => println!("Matched None"),
    }
}
```

Here, `Some` destructures the `Option`. The `&x` matches the reference inside the `Some`. This lets you extract the value `x` as a plain integer (i32 in this case).

## Moving and Borrowing

The following information is based on this example:

```rust
use ferris_says::say;
use std::io::{stdout, BufWriter};

fn main() {
    let message: String = String::from("Hello fellow Rustaceans!");
    let width: usize = message.chars().count();

    let mut writer = BufWriter::new(stdout());
    say(&message, width, &mut writer).unwrap();
}
```

In Rust, values can be passed to functions either by moving or by borrowing. These are key concepts in Rust's ownership system:

- Moving: When you pass a value to a function without a reference (e.g., just `message`), Rust assumes a move of ownership. After the move, you can't use the original variable unless the ownership is returned. This ensures memory safety but can be restrictive if you want to use the variable again after the function call.

- Borrowing: By passing a reference (`&message`), you borrow the value without transferring ownership. The function can use the value, but the original owner (in this case, the main function) retains ownership and can continue to use it after the function call. This is a non-destructive way to pass values to functions.

In your example, `say` needs to read `message` but doesn't need to own it. Using a reference (`&message`) is more efficient as it avoids unnecessary data copying and maintains the ability to use `message` later in the main function.

## Vec<T>

[Vector API Documentation](https://doc.rust-lang.org/std/vec/struct.Vec.html)

```rs
let mut v = vec![1, 2, 3, 4, 5];

let first = &v[0];

v.push(6);

println!("The first element is: {first}");
```

The code looks like it should work: why should a reference to the first element care about changes at the end of the vector? This error is due to the way vectors work: because vectors put the values next to each other in memory, adding a new element onto the end of the vector might require allocating new memory and copying the old elements to the new space, if there isn’t enough room to put all the elements next to each other where the vector is currently stored. In that case, the reference to the first element would be pointing to deallocated memory. The borrowing rules prevent programs from ending up in that situation.

## The `Copy` Trait

Types like i32, f64, char, and other simple, fixed-size types implement the Copy trait. These types represent simple values that can be easily duplicated in memory without any additional overhead or side effects. Because of this, when you use such a type in assignments, function calls, or returns, Rust will implicitly make a copy of the value.

This behavior influences how you use these types in your code:

- No Need for Borrowing for Copy: You don't need to borrow (&) an i32 when passing it to a function because passing by value is just as efficient due to the Copy trait. The value is automatically copied, and the original and the copy can be used independently.
- Simplifies Usage: This simplification means you don't have to think about lifetimes or mutable references for simple scalar values, making code easier to write and reason about.

## Loop Unrolling

There was context given which is not provided here.

Loop unrolling is a common optimization technique where the compiler transforms a loop into a sequence of repeated statements. This eliminates the overhead associated with the loop control, such as incrementing counters and evaluating termination conditions. In this specific case, Rust knows there are exactly 12 iterations (a fixed number), so it unrolls the loop completely, generating the equivalent of 12 separate but similar operations in the assembly code. This leads to faster execution but at the cost of potentially larger code size.

## Storing Values in Registers

There was context given which is not provided here.

Registers are the fastest type of memory available in a computer architecture. By storing variables directly in registers, Rust minimizes the need to access slower memory types (like RAM). This is particularly effective in tight loops or frequently accessed variables within performance-critical code. In the described Rust implementation, all coefficients are stored in registers, which speeds up the access time significantly during computations.

## Elimination of Bounds Checks

Normally, accessing an array would require bounds checks at runtime to prevent out-of-bounds errors, which can be a source of significant overhead, especially in loops. Rust is capable of ensuring memory safety at compile time through its ownership and types system, along with its borrowing rules. In cases where the compiler can definitively determine that all accesses are within valid bounds, it can safely eliminate these runtime checks.

## General Explanation of Pointers

Source and more information: https://doc.rust-lang.org/book/ch15-00-smart-pointers.html

A pointer is a general concept for a variable that contains an address in memory. This address refers to, or “points at,” some other data. The most common kind of pointer in Rust is a reference, which you learned about in Chapter 4. References are indicated by the & symbol and borrow the value they point to. They don’t have any special capabilities other than referring to data, and have no overhead.

Smart pointers, on the other hand, are data structures that act like a pointer but also have additional metadata and capabilities.

## Smart Pointers in General

A smart pointer is a data structure that not only acts like a pointer but also has additional metadata and capabilities. Smart pointers manage the lifecycle of the object they point to through automated reference counting, ownership rules, and other mechanisms. Rust's standard library provides several types of smart pointers, including `Box`, `Rc`, and `Arc`.

- `Box<T>`: Used for heap allocation. It provides ownership for the data it points to and deallocates the data when the Box goes out of scope.
- `Rc<T>`: A reference-counted smart pointer for single-threaded scenarios where multiple ownership is required. `Rc` stands for Reference Counted. It’s used when you need shared ownership but don’t require interior mutability. It’s immutable by default.
- `RefCell<T>` (Interior Mutability): Allows mutable borrowing at runtime, even if the `RefCell<T>` itself is immutable. It enforces borrowing rules dynamically (at runtime), unlike &mut T which enforces them at compile time.
  - `Rc<RefCell<T>>` is a common pattern where `Rc<T>` provides shared ownership, and `RefCell<T>` allows interior mutability.
- `Arc<T>`: An atomically reference-counted smart pointer. It is designed for sharing immutable data across threads safely. By itself, `Arc<T>` is not mutable in the sense that it does not allow you to modify the inner `T` directly. This is because multiple threads could hold a reference at once, so Rust prevents direct mutation to guarantee thread safety.
- `Mutex` is used to ensure that only one thread can mutate the data at a time. It basically locks it for one thread so no other threads can change that value while it's locked.
  - For shared mutability: `Arc<Mutex<T>>` allows safe, synchronized mutable access or `Arc<RwLock<T>>` allows multiple readers or one writer at a time.

**Dynamic Dispatch with dyn Error**
The `dyn Error` syntax in Rust is used to create trait objects. A trait object is a way of achieving dynamic dispatch in Rust, allowing you to call methods on types that implement a particular trait without knowing the exact type at compile time.

- `dyn Error` is a trait object that allows you to handle different error types uniformly. Since the exact type of error might not be known at compile time, you use `dyn Error` for dynamic dispatch.
- Types implementing traits can have different sizes, making them "unsized" types. Rust needs to know the size of every type at compile time for stack allocation. Using `Box<dyn Error>` allocates the error on the heap, providing a fixed-size pointer on the stack.
- Many async functions and libraries work with different types of errors. `Box<dyn Error>` provides a convenient way to return errors of any type that implements the Error trait, making it easier to write generic code.

## Box<T>

Source: https://doc.rust-lang.org/book/ch15-01-box.html

Boxes don’t have performance overhead, other than storing their data on the heap instead of on the stack. But they don’t have many extra capabilities either. You’ll use them most often in these situations:

- When you have a type whose size can’t be known at compile time and you want to use a value of that type in a context that requires an exact size.
- When you have a large amount of data and you want to transfer ownership but ensure the data won’t be copied when you do so.
- When you want to own a value and you care only that it’s a type that implements a particular trait rather than being of a specific type.

Boxes provide only the indirection and heap allocation; they don’t have any other special capabilities, like other smart pointer types. They also don’t have the performance overhead that these special capabilities incur, so they can be useful in cases like the cons list where the indirection is the only feature we need.

### `Box<dyn Error>`

The `Box<dyn Error>` part represents the type of value that is returned in the Err variant of the Result. Let's break this down further:

- Box: A heap-allocated smart pointer provided by the Rust standard library. Box is used here to allocate the error value on the heap and provide a reference to it.
- dyn: Stands for "dynamic". It indicates that the type is a trait object, meaning the concrete type will be determined at runtime.
- Error: A trait from the std::error module that represents error types.

So, `Box<dyn Error>` is a heap-allocated pointer to a type that implements the Error trait. This allows for dynamic dispatch of error types, enabling the function to return different types of errors that all conform to the Error trait.

## Drop Trait

Source: https://doc.rust-lang.org/book/ch15-03-drop.html

Implementing the Drop trait on a struct to configure the custom cleanup code after the instance went out of scope:

```rs
struct CustomSmartPointer {
    data: String,
}

impl Drop for CustomSmartPointer {
    fn drop(&mut self) {
        println!("Dropping CustomSmartPointer with data `{}`!", self.data);
    }
}

fn main() {
    let c = CustomSmartPointer {
        data: String::from("my stuff"),
    };
    let d = CustomSmartPointer {
        data: String::from("other stuff"),
    };
    println!("CustomSmartPointers created.");
}
```

## Message Passing with Multiple Threads

Source and more information: https://doc.rust-lang.org/book/ch16-02-message-passing.html

One increasingly popular approach to ensuring safe concurrency is message passing, where threads or actors communicate by sending each other messages containing data. Here’s the idea in a slogan from the Go language documentation: “Do not communicate by sharing memory; instead, share memory by communicating.”

To accomplish message-sending concurrency, Rust's standard library provides an implementation of channels. A channel is a general programming concept by which data is sent from one thread to another.

You can imagine a channel in programming as being like a directional channel of water, such as a stream or a river. If you put something like a rubber duck into a river, it will travel downstream to the end of the waterway.

A channel has two halves: a transmitter and a receiver. The transmitter half is the upstream location where you put rubber ducks into the river, and the receiver half is where the rubber duck ends up downstream. One part of your code calls methods on the transmitter with the data you want to send, and another part checks the receiving end for arriving messages. A channel is said to be closed if either the transmitter or receiver half is dropped.

## `thread::spawn` and `tokio::spawn`

**thread::spawn (Standard Threads):**

- Usage: Directly spawns a new OS thread.
- Threading: Each call to thread::spawn creates a separate operating system (OS) thread.
- Blocking: OS threads are heavyweight, which means they come with the cost of thread management and context switching.
- Performance: More threads result in higher overhead due to the OS's need to manage them (especially for large numbers of threads).
- Concurrency: Works well for CPU-bound tasks that can run in parallel, but may be inefficient for tasks that don’t need full threads, like I/O-bound tasks.

**tokio::spawn (Async Task on Tokio Runtime)**

- Usage: Spawns an asynchronous task that runs on Tokio's runtime, which can use a thread pool.
- Threading: By default, Tokio runs tasks on a thread pool, and tasks are typically scheduled on threads as needed. Tasks are not bound to specific threads.
- Blocking: Tasks spawned via tokio::spawn are lightweight async tasks that run cooperatively (concurrently) rather than using full OS threads. Async tasks yield control when they are awaiting I/O, making efficient use of a single or a small number of threads.
- Performance: Much more efficient for I/O-bound tasks (e.g., waiting on network requests, file I/O), as tasks don’t block the thread while waiting. Tasks are "farmed out" to a small number of threads and run until they need to await something, at which point another task can run.
- Concurrency: Works well for I/O-bound tasks and can handle many tasks concurrently on a small number of threads without significant overhead.

## Diesel

To set up Diesel it is recommended to use the diesel_cli which will help generating and running migrations or also just set up the project in general (`diesel setup`):

`cargo install diesel_cli --no-default-features --features postgres`

Have in mind, that you need postgreSQL installed for this (even if you don't use the CLI you will need to have it installed when using PostgreSQL), since it's reliant on specific PostgreSQL files.

To make this work, you will also have to set up environment variables on your system (example values below):

`LIBPQ_LIB_DIR=C:\Program Files\PostgreSQL\16\lib`
`LIBPQ_INCLUDE_DIR=C:\Program Files\PostgreSQL\16\include`

Also include the `bin` and `lib` directories to PATH:

- `C:\Program Files\PostgreSQL\16\bin`
- `C:\Program Files\PostgreSQL\16\lib`

If you still get errors, try setting the `PQ_LIB_STATIC` environment variable on your system:

- `PQ_LIB_STATIC=1`

Afterwards, you will need to adjust the migration file according to your needs (example below):

```rs
CREATE TABLE lands (
    id SERIAL PRIMARY KEY,
    token_id VARCHAR NOT NULL,
    owner VARCHAR,
    land_type VARCHAR,
    row INT,
    col INT,
    current_price_usd FLOAT NOT NULL,
    UNIQUE(token_id, current_price_usd)
);
```

Create the models and schemas (examples below):

**src/schema.rs:**

```rs
use diesel::table;

table! {
    lands (id) {
        id -> Int4,
        token_id -> Varchar,
        owner -> Nullable<Varchar>,
        land_type -> Nullable<Varchar>,
        row -> Nullable<Int4>,
        col -> Nullable<Int4>,
        current_price_usd -> Float8,
    }
}
```

**src/models.rs:**

```rs
use crate::schema::lands;
use diesel::{Insertable, Queryable};
use serde::{Deserialize, Serialize};

#[derive(Queryable, Deserialize, Serialize, Debug)]
pub struct Land {
    pub id: i32,
    pub token_id: String,
    pub owner: Option<String>,
    pub land_type: Option<String>,
    pub row: Option<i32>,
    pub col: Option<i32>,
    pub current_price_usd: f64,
}

#[derive(Insertable, Deserialize, Serialize, Debug)]
#[table_name = "lands"]
pub struct NewLand {
    pub token_id: String,
    pub owner: Option<String>,
    pub land_type: Option<String>,
    pub row: Option<i32>,
    pub col: Option<i32>,
    pub current_price_usd: f64,
}
```

If you are familiar with Nest.js and Mikroorm, for example, you can imagine the schemas being the entities and the models being the DTOs in some way or another.

## Struct vs. HashMap

_Use Cases for struct:_

- When you have a fixed number of fields known at compile time (e.g., user profiles, configuration settings).
- When you need type safety and want each field to have its own type.
- When performance is important because struct fields are stored in contiguous memory and access is very fast.
- When you want to model objects with specific attributes (e.g., a Point, Rectangle, User, etc.).

_Use Cases for HashMap:_

- When you need to store dynamic data where the keys are determined at runtime.
- When you need to look up values based on a key (e.g., caching, storing user preferences, word frequency counts).
- When you don't know ahead of time the exact set of keys or the data structure needs to change often.
- When you need flexibility and are willing to sacrifice some performance for it (e.g., configurations loaded from a file, dynamic settings).

| Feature              | `struct`                                              | `HashMap`                                                    |
| -------------------- | ----------------------------------------------------- | ------------------------------------------------------------ |
| **Fields/Keys**      | Fixed, known at compile time                          | Dynamic, added at runtime                                    |
| **Field Access**     | Fast, direct field access                             | Slower, requires key hashing and lookup                      |
| **Type Safety**      | Enforced, each field has its own type                 | All keys and values must have same type                      |
| **Memory Layout**    | Contiguous, efficient                                 | Non-contiguous, involves hashing                             |
| **Flexibility**      | Rigid, fields are static                              | Flexible, keys and values can be added or removed            |
| **Common Use Cases** | Modeling well-defined objects (e.g., `User`, `Point`) | Storing dynamic key-value data (e.g., caching, dictionaries) |

## `&dyn` vs. `Box<dyn>`

**Use &dyn (Trait Object as a Reference) When:**

- Ownership is not required: You only need a borrowed reference to the trait object.
- No heap allocation is needed: The reference points to an object that exists elsewhere, either on the stack or heap.
- Short-lived interactions: The lifetime of the reference is tied to the scope in which it is used.
- Low-overhead dynamic dispatch: Since it doesn't involve heap allocation, it's lightweight

**Example:**

```rs
fn print_sound(animal: &dyn Animal) {
    animal.make_sound();
}
```

**Use Box<dyn> (Heap-Allocated Trait Object) When:**

- You need ownership: The function or structure owning the Box<dyn> takes responsibility for the trait object’s lifetime and deallocation.
- Heap allocation is acceptable: The trait object is stored on the heap, allowing it to outlive its scope or be moved around freely.
- Dynamic polymorphism with longer lifetimes: For example, storing different types in a collection or returning a trait object from a function.

**Example:**

```rs
fn get_animal() -> Box<dyn Animal> {
    Box::new(Dog) // Ownership of `Dog` is transferred to the caller
}
```

| Feature      | `&dyn`                    | `Box<dyn>`                 |
| ------------ | ------------------------- | -------------------------- |
| Ownership    | Borrowed (doesn't own)    | Owned (takes ownership)    |
| Lifetime     | Scoped to the borrow      | Tied to the `Box`          |
| Allocation   | No additional allocation  | Heap-allocated             |
| Polymorphism | Supports dynamic dispatch | Supports dynamic dispatch  |
| Mutability   | Requires `&mut dyn`       | Can own a mutable object   |
| Use Case     | Temporary or shared usage | Long-lived or transferable |

## Borrowing Rules

1. **Ownership Rules**
   Each value in Rust has one owner.
   When the owner goes out of scope, the value is dropped.
   Ownership can be moved but not copied (unless the type implements Copy).
2. **Borrowing Rules**
   You can have one mutable reference (&mut T) or any number of immutable references (&T), but not both at the same time.
   References must always be valid (no use-after-free).
3. **Mutable Borrowing (&mut T)**
   Only one &mut T reference to a value is allowed at a time.
   The mutable reference must not exist while immutable references (&T) exist.
4. **Immutable Borrowing (&T)**
   Multiple &T references are allowed as long as no &mut T exists.
5. **Lifetimes and Borrowing**
   A reference must not outlive the data it points to.
   Rust prevents dangling references (e.g., returning a reference to a local variable).
   These rules ensure safe memory access without a garbage collector.
