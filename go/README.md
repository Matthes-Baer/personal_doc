# Go

## Courses
- https://www.boot.dev/lessons/224252be-adc9-452f-8ed0-0b305b25d0cb

## General Information
- The walrus operator, `:=`, declares a new variable and assigns a value to it in one line. It can't be used outside of a function (in the global/package scope).
- Go programs are fairly lightweight. Each program includes a small amount of extra code that’s included in the executable binary called the Go Runtime. One of the purposes of the Go runtime is to clean up unused memory at runtime. It includes a garbage collector that automatically frees up memory that’s no longer in use. 

As a general rule, Java programs use more memory than comparable Go programs. There are several reasons for this, but one of them is that Java uses a virtual machine to interpret bytecode at runtime and typically allocates more on the heap.

On the other hand, Rust and C programs use slightly less memory than Go programs because more control is given to the developer to optimize the memory usage of the program. The Go runtime just handles it for us automatically.
- On of the main purposes of the Go Runtime (which is within each Go executable), is to cleanup unused memory (an automated process)
- Constants can be primitive types like strings, integers, booleans and floats. They can not be more complex types like slices, maps and structs. You cannot declare a constant that can only be computed at run-time like you can in JavaScript. (`time.Now()` would break)


## Helpful Methods
- `fmt.Printf()` - Prints a formatted string to standard out (does not automatically end with a newline (\n))
- `fmt.Sprintf()` - Returns the formatted string (does automatically end with a newline (\n))


## Code Examples

### Same Line Declarations
```go
averageOpenRate, displayMessage := .23, "is the average open rate of your messages"
```

### Formatting Strings
```go
// %v for all variables (basically the default)
s := fmt.Sprintf("I am %v years old", 10)
// I am 10 years old

s := fmt.Sprintf("I am %v years old", "way too many")
// I am way too many years old

// %s for strings
s := fmt.Sprintf("I am %s years old", "way too many")
// I am way too many years old

// %d for integers
s := fmt.Sprintf("I am %d years old", 10)
// I am 10 years old

// %f for floats
s := fmt.Sprintf("I am %f years old", 10.523)
// I am 10.523000 years old

// The ".2" rounds the number to 2 decimal places
s := fmt.Sprintf("I am %.2f years old", 10.523)
// I am 10.52 years old
```

