# Rust

This section covers information about the programming language Rust.

## Useful Rust Lines

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

## Useful Methods

### String Methods

- len() (String, &str)
- chars() (String, &str)
- bytes() (String, &str)
- is_empty() (String, &str)
- contains() (String, &str)
- starts_with() (String, &str)
- ends_with() (String, &str)
- split() (String, &str)
- trim() (String, &str)
- to_lowercase() (String, &str)
- to_uppercase() (String, &str)

### Vector Methods

- len() (Vec)
- is_empty() (Vec)
- push() (Vec)
- pop() (Vec)
- contains() (Vec)
- iter() (Vec)
- extend() (Vec)
- sort() (Vec)
- sort_by() (Vec)
- sort_by_key() (Vec)
- map() (Vec, Iter)
- filter() (Vec, Iter)
- collect() (Vec, Iter)
- find() (Vec, Iter)
- fold() (Vec, Iter)
- for_each() (Vec, Iter)
- any() (Vec, Iter)
- all() (Vec, Iter)
- take() (Vec, Iter)
- skip() (Vec, Iter)
- enumerate() (Vec, Iter)
- zip() (Vec, Iter)

### HashMap Methods

- insert() (HashMap)
- get() (HashMap)
- contains_key() (HashMap)
- remove() (HashMap)
- keys() (HashMap)
- values() (HashMap)
- iter() (HashMap)
- iter_mut() (HashMap)

### Result and Option Methods

- unwrap() (Option, Result)
- unwrap_or() (Option, Result)
- is_some() (Option)
- is_ok() (Result)
- is_err() (Result)
- map() (Option, Result)
- map_err() (Result)
- and_then() (Option, Result)
- or_else() (Option, Result)
- ok() (Result)
- err() (Result)
- as_ref() (Option, Result)

### Iterator Methods

- next() (Iterator)
- map() (Iterator)
- filter() (Iterator)
- collect() (Iterator)
- find() (Iterator)
- fold() (Iterator)
- for_each() (Iterator)
- any() (Iterator)
- all() (Iterator)
- take() (Iterator)
- skip() (Iterator)
- enumerate() (Iterator) - returns iterator of tuples with each tuple containing a reference to the index and a reference to the value
- zip() (Iterator)
- flat_map() (Iterator)
- cloned() (Iterator)
- cycle() (Iterator)

## Useful Crates

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
- **Fn, FnMut, FnOnce**: For types that can be invoked as functions, representing callable closures or function-like types with different mutability levels.
- **Queryable** (Diesel): Allows a type to be built from database query results.
- **Insertable** (Diesel): Enables a type to be inserted into a database table.
- **Identifiable** (Diesel): Marks a type as having a primary key for database use.
- **AsChangeset** (Diesel): Allows updating database rows with a type.

## General Information

- The **Arc** type is used to share ownership of the data across multiple threads.
- The **Mutex** type is used to ensure that only one thread can mutate the data at a time.
- The **mod** keyword declares a module. Used to tell Rust to look for the corresponding file or directory (like `mod routes` or `mod services` in the `main.rs` file).
- The **use** keyword brings items into scope, allowing you to use them without fully qualifying their paths.
- Use **pub** to make functions, structs, or modules public. Without pub, items are private to the module.
- Use **pub use** to re-export items, making them accessible through the parent module.
- By implementing a "Trait" for a type, that type gains the ability to utilize the methods defined by the trait. This enables **polymorphism**, where different types can be treated interchangeably as long as they implement the same trait.

## Code examples

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

- Rust's ownership and borrowing system prevents many pointer-related issues by enforcing strict rules at compile time (like preventing dangling pointers).

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

2. Pattern Matching/Destructuring: When used in the context of a pattern (like in function arguments, let bindings, or match arms), & can actually perform a dereference operation. This might seem counterintuitive, but it's a shorthand provided by Rust's pattern matching capabilities.
   For example, in a function call like function(&x), &x is passing a reference to x. However, in the function signature, if you see something like fn function(&x: &i32), the & in &x is actually dereferencing the passed reference to directly work with the value in the function body, without needing to manually dereference it using \*.

## Pattern Matching

The following explanation is based on this code example:

```rs
    let my_array = [1, 2, 3, 4, 5];
    let slice = &my_array[..];

    for i in slice {
        println!("{}", i)
    }
```

In Rust, when you write for i in slice, i is a reference to the element of the array,
so it has the type &i32 because the array slice &my_array[..] is a reference to the array elements.

When you use for &i in slice, you're using pattern matching in the loop.
In this case, the &i pattern means that you are destructuring the reference &i32 into the value it points to, which is of type i32.

**Here's what's happening in detail:**

- slice is a reference to an array (i.e., &[i32]).
- When you iterate over slice using for i in slice, each element is of type &i32 (a reference to an integer).
- By using the pattern for &i in slice, you're telling Rust to dereference the &i32 value to get the i32 directly.

So, instead of getting a reference to each element (&i32), you pattern match to extract the value (i32).

The reason it doesn't become &&i32 is that pattern matching with &i destructures one level of reference, converting &i32 into i32.

## Understanding `mut` in Rust

mut stands for mutable. It's used to declare that a variable can be modified after its initial declaration. In Rust, variables are immutable by default, meaning once a value is bound to a name, you can’t change that value. To allow a variable to be mutable, you prepend it with mut.

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

The code look like it should work: why should a reference to the first element care about changes at the end of the vector? This error is due to the way vectors work: because vectors put the values next to each other in memory, adding a new element onto the end of the vector might require allocating new memory and copying the old elements to the new space, if there isn’t enough room to put all the elements next to each other where the vector is currently stored. In that case, the reference to the first element would be pointing to deallocated memory. The borrowing rules prevent programs from ending up in that situation.

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

## General Explanation of Smart Pointers

Source and more information: https://doc.rust-lang.org/book/ch15-00-smart-pointers.html

A pointer is a general concept for a variable that contains an address in memory. This address refers to, or “points at,” some other data. The most common kind of pointer in Rust is a reference, which you learned about in Chapter 4. References are indicated by the & symbol and borrow the value they point to. They don’t have any special capabilities other than referring to data, and have no overhead.

Smart pointers, on the other hand, are data structures that act like a pointer but also have additional metadata and capabilities.

## Smart Pointers in General

A smart pointer is a data structure that not only acts like a pointer but also has additional metadata and capabilities. Smart pointers manage the lifecycle of the object they point to through automated reference counting, ownership rules, and other mechanisms. Rust's standard library provides several types of smart pointers, including `Box`, `Rc`, and `Arc`.

- `Box<T>`: Used for heap allocation. It provides ownership for the data it points to and deallocates the data when the Box goes out of scope.#
- `Rc<T>`: A reference-counted smart pointer for single-threaded scenarios where multiple ownership is required. `Rc` stands for Reference Counted.
- `Arc<T>`: An atomically reference-counted smart pointer suitable for multi-threaded scenarios where multiple ownership is required. `Arc` stands for Atomic Reference Counted.

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
