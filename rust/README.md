# Rust

This section covers information about the programming language Rust.

## Useful Rust Lines

- convert a number to it's binary representation: `let binary_repr = format!("{:b}", n);`
- convert a binary number to it's decimal representation: `match isize::from_str_radix(&reversed_binary, 2) { ... handle Ok() and Err() ... }`
- get sum from all Vector elements: `let sum: i32 = (1..=n).collect().iter().sum();`
- get product from all Vector elements: `let product: i32 = (1..=n).collect().iter().product();`

## Short Overviews

- The **Arc** type is used to share ownership of the data across multiple threads.
- The **Mutex** type is used to ensure that only one thread can mutate the data at a time.
- The **mod** keyword declares a module. Used to tell Rust to look for the corresponding file or directory (like `mod routes` or `mod services` in the `main.rs` file).
- The **use** keyword brings items into scope, allowing you to use them without fully qualifying their paths.
- Use **pub** to make functions, structs, or modules public. Without pub, items are private to the module.
- Use **pub use** to re-export items, making them accessible through the parent module.

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

## Example

Consider a String type in Rust. When you create a String, the struct that represents the String (which includes the pointer, length, and capacity) is stored on the stack. The actual contents of the string, however, are stored on the heap. The pointer in the String struct points to this heap-allocated memory where the characters of the string are stored.

```js
let s = String::from("hello");
```

In this example, s is a variable on the stack that contains a String struct. This struct contains a pointer to the heap where the actual "hello" string is stored. The String struct itself might contain more than just a pointer (like length and capacity), but the crucial part for this discussion is that the character data is on the heap, and s on the stack points to it.

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

## Box<T>

Source: https://doc.rust-lang.org/book/ch15-01-box.html

Boxes don’t have performance overhead, other than storing their data on the heap instead of on the stack. But they don’t have many extra capabilities either. You’ll use them most often in these situations:

- When you have a type whose size can’t be known at compile time and you want to use a value of that type in a context that requires an exact size.
- When you have a large amount of data and you want to transfer ownership but ensure the data won’t be copied when you do so.
- When you want to own a value and you care only that it’s a type that implements a particular trait rather than being of a specific type.

Boxes provide only the indirection and heap allocation; they don’t have any other special capabilities, like other smart pointer types. They also don’t have the performance overhead that these special capabilities incur, so they can be useful in cases like the cons list where the indirection is the only feature we need.

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
