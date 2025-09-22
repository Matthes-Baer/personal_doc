# Go

## Useful Links
- [Install Go](https://go.dev/doc/install)
- [Go Project Structure/Layout](https://github.com/golang-standards/project-layout)
- [Learn Go Fast: Full Tutorial (including building an API project example)](https://www.youtube.com/watch?v=8uiZC0l4Ajw)
- [Boot Dev Tutorial](https://www.boot.dev/lessons/224252be-adc9-452f-8ed0-0b305b25d0cb)
- [Learn Go as JavaScript Developer](https://prateeksurana.me/blog/guide-to-go-for-javascript-developers/?utm_source=tldrwebdev)
- [Defer, Panic, And Recover](https://go.dev/blog/defer-panic-and-recover)
- [Tricky Slices - append() and capacity](https://www.boot.dev/lessons/f100f470-4a34-4c10-8035-551e1a8e1834)


## Useful Functions

- append   -> adds elements to a slice, returns the updated slice
- cap      -> returns the capacity of a slice, array, or channel
- close    -> closes a channel, signaling no more values will be sent
- complex  -> creates a complex number from two floats (real, imaginary)
- copy     -> copies elements from one slice to another
- delete   -> removes an element from a map by key
- imag     -> returns the imaginary part of a complex number
- len      -> returns the length of a string, slice, array, map, or channel
- make     -> allocates and initializes slices, maps, or channels
- new      -> allocates memory for a value, returns a pointer to it
- panic    -> stops execution and begins panicking
- print*   -> prints values to stdout (for debugging only, not for production)
- println* -> like print, but adds a newline (debugging only)
- real     -> returns the real part of a complex number
- recover  -> regains control of a panicking goroutine (used in defer)


## General Information
- In Go, function arguments are passed by value by default, meaning the function works with a copy of the variable, leaving the original unchanged. For example, passing an int to a function won’t modify its value outside the function. To allow functions to update the original variable, Go uses pointers, which pass the variable’s memory address instead of a copy, enabling direct modification of the original data. This pattern is especially useful when working with larger or composite types, like structs, as it avoids unnecessary copying and improves performance. When accessing struct fields through a pointer, Go simplifies the syntax by allowing direct field access with the selector expression (e.g., analytics.MessagesTotal), which is shorthand for (*analytics).MessagesTotal. This makes pointer usage in Go more ergonomic and efficient while keeping code readable. Pointers are dangerous since they can point to nothing. Always check if a pointer is nil before using it to avoid panics (effectively crashing your application). 
In Go, all function arguments are passed by value, but the effect differs depending on the type: basic types (ints, floats, bools, strings, structs, arrays) are copied directly, so changes inside a function don’t affect the caller’s copy; in contrast, reference types (slices, maps, channels, functions, interfaces) are passed by value too, but what’s copied is a small descriptor pointing to shared underlying data, so modifications to that data are visible outside the function; if you want structs or arrays to behave this way, you explicitly pass a pointer to them.

- In Go, a map is a built-in data structure that provides an efficient way to associate keys with values, similar to hash tables or dictionaries in other languages. You declare them using the syntax map[KeyType]ValueType. The key type can be any type that is comparable, meaning it supports equality operators (== and !=). This includes basic types like strings, integers, booleans, and pointers, as well as structs and arrays, provided all their fields or elements are also comparable. However, slices, maps, and functions cannot be used as keys because they are not comparable. Values, on the other hand, can be of any type, including slices, maps, or functions.        
Maps in Go don’t have methods in the object-oriented sense, but they work with several important built-in operations. You can add or update an entry with m[key] = value, retrieve a value with val := m[key], and delete entries using delete(m, key). Accessing a key that doesn’t exist returns the zero value of the value type, so Go provides the “comma ok” idiom: val, ok := m[key]—where ok is a boolean that’s true if the key exists. Iteration is done using for k, v := range m, though the order of iteration is deliberately random. You can get the number of entries with len(m), but there’s no built-in method for checking emptiness aside from comparing len(m) == 0. Maps are reference types, so copying or passing them around doesn’t duplicate the data, only the reference. When having a type like `testMap := map[string]int{}` you can just do like `testMap["name"]++` - you don't have to check if the key exists because due to the `int` value it just starts with it's zero value (for `int` it's `0`)

- In Go, you can check the memory address of a variable using the address-of operator `&`. For example, `&x` gives you the memory address where `x` is stored. You can also store this in a pointer variable, and if you dereference it with `*`, you get back the value at that address. Inspecting memory addresses can be useful for understanding whether two variables point to the same underlying data (like when working with slices, maps, or pointers). However, the exact value of the memory address itself isn’t typically meaningful in application code—it’s more of a debugging or low-level optimization tool.

- Go does not have a `while` loop, but you can make use of a `for` loop with just a condition (`for CONDITION { ... }`)

- The built-in error interface defines only one method `Error() string`, which returns the error message. You can create custom error types by defining structs that implement this method. Once implemented, your custom struct can be used just like a regular error (for example, as a function’s return type of `Error`). There is also the `errors` package provided by the Go standard library that you can import to have some helpers when dealing with errors. `fmt.Errorf` can be used to wrap an error with additional context. Don't use panic, use error values for "normal" error handling, and otherwise use `log.Fatal` to print a message and exit the program afterwards.

- Interfaces are implemented implicitly, there is no explicit declaration for interfaces with an `implements` keyword or similar.

- Use `"go.formatTool": "goimports"` in your VS Code settings to make the Go formatting work (pick the formatter, you want to use). `"editor.defaultFormatter": "golang.go"` within the `"[go]"` section might also be needed if not already added. `"go.toolsManagement.autoUpdate": true` is also part of my VS Code settings.

- In Go, the `cmd/` directory is commonly used to hold entry points for executables. When you run a command like `go build ./cmd`, Go compiles everything inside that folder belonging to the same package (usually package main). All `.go` files in the same package are treated as one unit, so you can split logic across multiple files, but only one `main()` function is allowed. The result is a single binary placed in the specified output path.
Go automatically resolves dependencies: if your cmd package imports other local packages (e.g., `internal/models`, `internal/helpers`), Go will also compile those. You don’t need to build them separately; they’re pulled in transitively as needed. The special `internal/ folder` ensures encapsulation — its packages can only be imported by code within the same module or subdirectories, preventing outside modules from depending on your internal logic.
You use the `pkg/` directory in Go when you want to expose code that is safe and intended for use by other applications or modules outside your project. Unlike `internal/`, which restricts visibility, anything placed in `pkg/` is publicly importable, making it a good place for shared libraries, utilities, or reusable components that might be valuable beyond your own project. In practice, `pkg/` is optional — some teams prefer putting all code under `internal/` to enforce strict boundaries — but if you anticipate that parts of your code could be reused by others (or even across your own projects), `pkg/` is the conventional home.
This structure encourages a clean separation: keep most of your logic inside `internal/` or `pkg/`, while `cmd/` contains minimal startup code that wires things together. That way, you can create multiple executables in the same project (e.g., `cmd/server`, `cmd/cli`) that share internal code.
In summary, `go build ./cmd` builds a single executable by compiling all files in that folder under package `main` along with all imported dependencies. The `internal/` folder is automatically included when imported, but it cannot be used externally. A typical Go project keeps executable entry points small and maintains reusable code in `internal/` or `pkg/`. This convention keeps projects modular, maintainable, and consistent with Go’s philosophy.

- In Go, project structure and package organization are more opinionated than in languages like Python or JavaScript. Commonly, projects use an `internal` folder for code that should not be imported outside the module, a `cmd` folder for executable entry points, and a models or similar package for shared data structures. Imports are always resolved relative to the module base path defined in go.mod, so you import using the full module path, not relative file paths. For example, if your module is `github.com/user/project`, you might import models as `github.com/user/project/internal/models`.
Go does not support wildcard imports like `import * as ...` in JavaScript or `from ... import *` in Python. Every imported package must have a unique name (usually derived from the folder name), and you use that name as a prefix when calling functions, types, or variables from the package. To simplify code or avoid naming collisions, Go allows aliases for imports, e.g., `import m "github.com/user/project/internal/models"`, letting you write `m.Result` instead of `models.Result`.
Finally, Go’s visibility rules are simple: identifiers (functions, types, constants, variables) are exported only if they start with an uppercase letter. Anything starting with a lowercase letter is private to the package. This convention replaces access modifiers like public or private in other languages, and helps maintain encapsulation within packages while keeping the API surface clean.

- When you create a file and rename it shortly after, it may happen that VS Code tells you that it doesn't know the new name, yet, and compares it with the previous file name (like "abc" and "abC"). In such a case you won't get any editing support (like syntax highlighting, auto-completion, etc.). To fix this, run `go clean -cache -modcache -i -r`, then refresh the window (or restart VS Code completely).

- In Go, pointers allow you to reference a value without copying it, which is useful for efficiency and for modifying the original value. Normally, when you have a pointer to a value, you would use the `*` operator to dereference it and access the underlying value. For example, if p is a `*Person`, writing `*p` gives you the Person value itself. However, Go has a convenience feature: when you call a method on a pointer, the language automatically dereferences it if needed. This means you can write `p.Method()` even if Method is defined on the value type rather than the pointer type. Go handles the dereferencing behind the scenes, so you rarely need to manually use `*selection` when calling methods — making code simpler and easier to read. You use pointers when you want to avoid copying large structs, modify a value in place across function calls or methods, or represent optional values that can be nil; essentially, pointers help you share and mutate data efficiently without duplicating memory.

- Goroutines are not OS threads — they’re lightweight, user-space threads managed by the Go runtime. When you create a goroutine, it doesn’t directly map to a new operating system thread. Instead, the Go scheduler runs many goroutines on a smaller pool of OS threads. The difference is that OS threads are “heavy”: they require a large, fixed stack and are scheduled by the operating system. Goroutines, on the other hand, start with a very small stack (just a few KB) that grows and shrinks as needed. This makes them extremely cheap to create — you can easily run thousands or even millions of goroutines in a single Go program. Behind the scenes, the Go scheduler multiplexes goroutines onto OS threads. If you have multiple CPU cores available, goroutines can be scheduled to run in parallel, but you don’t have to manage that yourself. You just write code using goroutines, and Go takes care of efficiently mapping them to threads. So, goroutines rely on OS threads under the hood for execution, but they are much lighter and more scalable than creating threads directly. That’s why Go is so good at handling high concurrency workloads. You use goroutines with channels when you need safe, concurrent execution where tasks run independently but still communicate or synchronize; channels provide a way to pass data between goroutines without explicit locking, making them ideal for coordinating work, streaming results, or building concurrent pipelines.

- When a function is uppercase in Go, it means that other modules can access it (public). If it is lowercase, it is private to the package/module.

- Goroutines are lightweight threads managed by the Go runtime, used to perform concurrent (not necessary via parallel execution (see explanation below)) tasks. When you prefix a function call with the `go` keyword, it runs that function asynchronously as a goroutine, allowing the rest of your program to continue executing without waiting for that function to finish. For example, `go doSomething()` launches `doSomething` in the background. Goroutines are much more memory-efficient than traditional threads, allowing you to run thousands or even millions concurrently. Under the hood, Go uses a scheduler to multiplex many goroutines onto a smaller number of OS threads, optimizing performance and resource usage. The scheduler handles when goroutines should run, pause, or resume, abstracting away the complexity of thread management. Because goroutines share memory space, communication and synchronization between them is often done using channels, a built-in feature of Go that allows safe data exchange between goroutines. This fits Go’s philosophy of "do not communicate by sharing memory; share memory by communicating."
  - Concurrency in goroutines means structuring your program so multiple tasks can make progress independently, often by switching between them efficiently on a single or few OS threads. Parallelism, on the other hand, means running multiple goroutines truly simultaneously on multiple CPU cores at the same time. So concurrency is about managing multiple tasks logically, while parallelism is about physically executing them simultaneously.
  - Whether Goroutines run in parallel depends on the Go runtime and how many CPU cores are available and utilized—if you have multiple cores and set `GOMAXPROCS` accordingly (By default, since Go 1.5, `GOMAXPROCS` is set to the number of logical CPUs detected (usually matches `$env:NUMBER_OF_PROCESSORS`)), goroutines can run in parallel across those cores. So, goroutines enable concurrency always, but parallelism only happens when the runtime schedules them on multiple OS threads running on multiple cores.

- Channels in Go are a way for goroutines to communicate and synchronize by sending and receiving typed data. Think of a channel as a pipe: one goroutine sends data into it, and another receives data out of it, using the `<-` operator. This lets you safely share information between concurrent tasks without explicit locking. Channels can be unbuffered, where sending blocks until the receiver is ready, or buffered, allowing sending to proceed up to a set capacity before blocking. This blocking behavior makes channels useful for coordinating work and ensuring goroutines stay in sync. You can also close channels to indicate no more data will be sent, allowing receivers to detect completion. In short, channels provide a simple, safe, and elegant way to handle communication between goroutines, making concurrent programming in Go easier to reason about -> they 1. hold data, 2. are thread safe, 3. listen for data

- In Go, when you pass a variable to a function by value (which is the default), the function receives a copy of that variable, not the original.

- Go has a garbage collector. Go automatically manages memory by tracking object lifetimes and reclaiming memory when values are no longer reachable, eliminating the need for manual memory management (like malloc and free in C). Go’s garbage collector is optimized for low-latency and is especially tuned for server workloads. This is one of Go’s key selling points—it provides concurrency and memory safety without the programmer worrying about freeing memory manually.

- In Go, a pointer holds the memory address/location of a variable rather than the actual value. You create a pointer by using the `&` operator to get the address of a variable (e.g. `p := &x`), and you access or modify the value at that address using the `*` operator, known as dereferencing (e.g., `*p = 10` changes the value of `x` through `p`). Go has no pointer arithmetic like C or C++ (addition or subtraction directly on pointers), which helps avoid common memory bugs. Pointers in Go are useful for modifying values in functions (since function arguments are passed by value by default), optimizing performance by avoiding unnecessary copying, and working with complex data structures like linked lists or trees. The zero value of a pointer is `nil`, and dereferencing a nil pointer causes a runtime panic.

- Go is a Statically Typed Language: This means that the type of a variable is known at compile time, and you must declare the type of a variable when you create it. This is different from dynamically typed languages like JavaScript, where types are determined at runtime.

- Go is a Strongly Typed Language: This means that you cannot perform operations on variables of different types without explicitly converting them. For example, you cannot add a string and an integer together without converting one of them to the other's type.

- Go code is compiled into machine code, which makes it fast and efficient. This is different from interpreted languages like JavaScript, where the code is executed line by line at runtime.

- Go has fast compilation times, which means that you can quickly build and run your code without waiting for long periods.

- In Go there are modules and packages. A module is a collection of related Go packages, and a package is a collection of Go source files that are compiled together. Modules are used to manage dependencies and versioning in Go projects.

- Go makes use of a special main package and a main function as the entry point of the program. The main package is where the program starts executing, and the main function is where the code begins. The main function must be defined in the main package for the program to run.

- Go follows a field after field memory layout for structs. By having a poorly designed order of fields like having a `uint8` type before a `uint16` type - this would lead to Go "align" the `uint16` field, effectively creating some padding (wasted space) to make up for the size difference between the two types; this helps with execution speed but you will have increased memory usage compared with having the proper order of first the `uint16` and then the `uint8` type - [boot.dev lesson on this](https://www.boot.dev/lessons/84de8a08-1f02-47fd-b0a9-cab314162722)
- Summary of What "Not Object-Oriented" Means in Go:
  - No classes: Instead, you have structs and methods.
  - No inheritance: You use composition (embedding structs) to combine behaviors.
  - Interfaces: Used for polymorphism, and they are implicitly satisfied based on method signatures.
  - Simpler model: Focuses on data and behavior with fewer language features to manage.

- The walrus operator, `:=`, declares a new variable and assigns a value to it in one line. It can't be used outside of a function (in the global/package scope).

- Go programs are fairly lightweight. Each program includes a small amount of extra code that’s included in the executable binary called the Go Runtime. One of the purposes of the Go runtime is to clean up unused memory at runtime. It includes a garbage collector that automatically frees up memory that’s no longer in use. As a general rule, Java programs use more memory than comparable Go programs. There are several reasons for this, but one of them is that Java uses a virtual machine to interpret bytecode at runtime and typically allocates more on the heap. On the other hand, Rust and C programs use slightly less memory than Go programs because more control is given to the developer to optimize the memory usage of the program. The Go runtime just handles it for us automatically.

- On of the main purposes of the Go Runtime (which is within each Go executable), is to cleanup unused memory (an automated process)

- Constants can be primitive types like strings, integers, booleans and floats. They can not be more complex types like slices, maps and structs. You cannot declare a constant that can only be computed at run-time like you can in JavaScript. (`time.Now()` would break)

- When you need to work with individual characters in a string, you should use the `rune` type. It breaks strings up into their individual characters, which can be more than one byte long.

- When using the `len()` function on a string, it returns the number of bytes in the string, not the number of characters. This is important to remember when dealing with multi-byte characters (like UTF-8 encoded characters) where the byte count may not equal the character count. In such cases, you may want to use the `utf8.RuneCountInString()` function from the `unicode/utf8` package to get the correct character count (runes (`rune`) are a separate type).

## Some Helpful Commands
- Initialize a new Go module: `go mod init <module-name>`
- Build the current module (only build, without directly running): `go build <path>`
- Build and run the current module: `go run <path>`

## Some Helpful Methods
- Prints without newline: `fmt.Print("hello")`
- Prints with newline: `fmt.Println("hello")`
- Formatted print: `fmt.Printf("Value: %d\n", 10)`
- Returns formatted string: `str := fmt.Sprintf("Hello %s", "Go")`
- Concatenates values to string: `str := fmt.Sprint("Hello", "World")`
- Concatenates with newline: `str := fmt.Sprintln("Hello", "World")`
- Create error with message: `err := fmt.Errorf("error: %v", "something went wrong")`
- Reads space-separated input: `fmt.Scan(&inputVar)`
- Reads until newline: `fmt.Scanln(&inputVar)`
- Parses formatted string into variables: `fmt.Sscanf("Age: 30", "Age: %d", &age)`
- Go syntax representation (structs, slices): `fmt.Printf("%#v\n", someVar)`
- Prints the type of variable: `fmt.Printf("%T\n", someVar)`

- Append elements to a slice: `slice = append(slice, newElement)`
- Append one slice to another: `slice = append(slice, slice2...)`
- Get length of a slice (current number of elements): `length := len(slice)`
- Get capacity of a slice (maximum number of elements it can hold without reallocating): `capacity := cap(slice)`
- Make slice with predefined length and capacity (length = 3, capacity = 8): `slice := make([]int, 3, 8)`
- Make a map with predefined length: `myMap := make(map[string]int)`
- Copy a slice (creating a new slice with its own underlying array and copying the elements from another slice into it - instead of only referencing to the same data): `copy(copySlice, original)`
- Cut/Remove element (manual way): `slice = append(slice[:index], slice[index+1:]...)`
- Clear slice (zero length, same capacity): `slice = slice[:0]`

- Delete a value from a map (by reference, so not return value): `delete(myMap, "key")`

## Code Examples

### Interfaces

Interfaces are abstract types that define behavior via method signatures, structs on the other hand are concrete data types used to group related fields.

At compile time, the Go compiler checks the methods of a type (e.g., Circle or Rectangle) and determines automatically whether it satisfies an interface. If all the methods of the interface are implemented by the type — it is compatible.
This is called structural typing (based on method structure), unlike Java/C#/C++ which use nominal typing (explicit declarations like implements). TypeScript uses structural typing as well.

```go
package main

import (
	"fmt"
	"math"
)

// Define an interface
type Shape interface {
	Area() float64
	Perimeter() float64
}

// Define a struct: Circle
type Circle struct {
	Radius float64
}

// Implement Shape interface for Circle
func (c Circle) Area() float64 {
	return math.Pi * c.Radius * c.Radius
}

func (c Circle) Perimeter() float64 {
	return 2 * math.Pi * c.Radius
}

// Define another struct: Rectangle
type Rectangle struct {
	Width, Height float64
}

// Implement Shape interface for Rectangle
func (r Rectangle) Area() float64 {
	return r.Width * r.Height
}

func (r Rectangle) Perimeter() float64 {
	return 2 * (r.Width + r.Height)
}

func printShapeInfo(s Shape) {
	fmt.Printf("Area: %.2f\n", s.Area())
	fmt.Printf("Perimeter: %.2f\n", s.Perimeter())
}

func main() {
	c := Circle{Radius: 5}
	r := Rectangle{Width: 4, Height: 6}

	fmt.Println("Circle:")
	printShapeInfo(c) // Compiler checks: does Circle have Area() and Perimeter()?

	fmt.Println("\nRectangle:")
	printShapeInfo(r) // Compiler checks: does Rectangle have Area() and Perimeter()?
}
```

### Structs

In Go, a struct is a composite data type that groups together fields (variables) under a single name. It’s used to model objects or data structures with multiple attributes.

```go
package main

import "fmt"

type Car struct {
    Brand string
    Year  int
}

func main() {
    myCar := Car{Brand: "Toyota", Year: 2020}
    fmt.Println("Car:", myCar.Brand, "Year:", myCar.Year)
}
```

### Struct Methods

Go is not an object-oriented language, but it allows you to define methods on structs. Methods are essentially functions with a special receiver parameter, which is placed before the function name. This approach enables you to attach behavior to structs, similar to how methods work with classes in object-oriented languages.

```go
package main

import "fmt"

// Define a struct
type Person struct {
    Name string
    Age  int
}

// Method with value receiver
func (p Person) Greet() {
    fmt.Printf("Hello, my name is %s and I am %d years old.\n", p.Name, p.Age)
}

// Method with pointer receiver (modifies the struct)
func (p *Person) HaveBirthday() {
    p.Age += 1
    fmt.Printf("Happy Birthday %s! You are now %d years old.\n", p.Name, p.Age)
}

func main() {
    // Create a new Person
    person := Person{Name: "Alice", Age: 30}

    // Call Greet method (does not modify the struct)
    person.Greet()

    // Call HaveBirthday method (modifies the struct)
    person.HaveBirthday()

    // Call Greet again to see the updated age
    person.Greet()
}
```

### Embedded Structs

In Go, embedded structs allow you to include one struct inside another, promoting its fields and methods to the outer struct. This is a way to achieve composition (a common alternative to inheritance in Go). The outer struct automatically gets access to the embedded struct's fields and methods as if they were its own.

```go
package main

import "fmt"

// Define a base struct
type Address struct {
    City    string
    Country string
}

// Define another struct embedding Address
type Person struct {
    Name string
    Age  int
    Address  // Embedded struct
}

// Method on Address
func (a Address) Location() string {
    return a.City + ", " + a.Country
}

func main() {
    // Create a Person
    p := Person{
        Name: "John",
        Age:  35,
        Address: Address{
            City:    "Berlin",
            Country: "Germany",
        },
    }

    // Access embedded fields directly
    fmt.Println(p.Name, "lives in", p.Location())  // Calls Address.Location()
    fmt.Println("City:", p.City)                  // Access City field directly
}
```

### Anonymous Structs

An anonymous struct is a struct without a named type. It’s useful for temporary data structures, especially in small scopes.

```go
package main

import "fmt"

func main() {
    person := struct {
        Name string
        Age  int
    }{
        Name: "Alice",
        Age:  28,
    }

    fmt.Println("Person:", person.Name, "Age:", person.Age)
}
```

### Closures

A closure in Go is a function that references variables from its surrounding scope, retaining access to those variables even after the surrounding function exits.

```go
package main

import "fmt"

func main() {
    counter := func() func() int {
        count := 0
        return func() int {
            count++
            return count
        }
    }()

    fmt.Println(counter()) // 1
    fmt.Println(counter()) // 2
    fmt.Println(counter()) // 3
}
```

### Defer

defer in Go postpones the execution of a function until the surrounding function returns. Deferred calls are executed in last-in, first-out (LIFO) order, making them useful for resource cleanup (like closing files, unlocking mutexes, etc.).

```go
package main

import "fmt"

func main() {
    fmt.Println("Start")

    defer fmt.Println("Deferred: runs after main function finishes")

    fmt.Println("End")
}


// Output:
// Start
// End
// Deferred: runs after main function finishes
```


### Named Return Values / Naked Returns

Go allows you to name return values in the function signature. A naked return lets you return these values without explicitly specifying them in the return statement. This can make code cleaner, especially when multiple values are being returned.

```go
package main

import "fmt"

// Named return values: result and message
func Multiply(a, b int) (result int, message string) {
    result = a * b
    message = fmt.Sprintf("The product of %d and %d is %d", a, b, result)
    return // naked return: returns result and message
}

func main() {
    res, msg := Multiply(3, 4)
    fmt.Println(msg, "| Result:", res)
}
```

### Return multiple values and get multiple values from a function

```go
func getPoint() (x int, y int) {
  return 3, 4
}

// you can also ignore values; this is not just a convention but a real language feature that completely discards the value
x, _ := getPoint()
```


### Multiple Parameters With Same Type

When multiple arguments are of the same type, and are next to each other in the function signature, the type only needs to be declared after the last argument.

```go
func addToDatabase(hp, damage int, name string) {
  // ?
}
```

### Same Line Declarations
```go
averageProcessRate, displayMessage := .23, "some_text"
```

### Formatting Strings

```go
package main

import "fmt"

func main() {
    x := 42
    f := 3.1415
    s := "GoLang"
    b := true

    fmt.Printf("%%v (default): %v\n", x)           // 42
    fmt.Printf("%%+v (struct with fields): %+v\n", struct{ Name string }{"John"}) // {Name:John}
    fmt.Printf("%%#v (Go syntax): %#v\n", struct{ Name string }{"John"}) // struct { Name string }{Name:"John"}

    fmt.Printf("\n=== Numbers ===\n")
    fmt.Printf("%%d (decimal int): %d\n", x)       // 42
    fmt.Printf("%%b (binary): %b\n", x)            // 101010
    fmt.Printf("%%o (octal): %o\n", x)             // 52
    fmt.Printf("%%x (hex lowercase): %x\n", x)     // 2a
    fmt.Printf("%%X (hex uppercase): %X\n", x)     // 2A

    fmt.Printf("\n=== Floating Point ===\n")
    fmt.Printf("%%f (float): %f\n", f)             // 3.141500
    fmt.Printf("%%.2f (float, 2 decimals): %.2f\n", f) // 3.14

    fmt.Printf("\n=== Strings ===\n")
    fmt.Printf("%%s (string): %s\n", s)            // GoLang
    fmt.Printf("%%q (quoted string): %q\n", s)     // "GoLang"
    fmt.Printf("%%c (character): %c\n", 65)        // A

    fmt.Printf("\n=== Boolean ===\n")
    fmt.Printf("%%t (boolean): %t\n", b)           // true

    fmt.Printf("\n=== Pointers ===\n")
    fmt.Printf("%%p (pointer): %p\n", &x)          // 0x...

    fmt.Printf("\n=== Width and Alignment ===\n")
    fmt.Printf("%%6d (right-aligned, width 6): %6d\n", x)  //    42
    fmt.Printf("%%-6d (left-aligned, width 6): %-6dEND\n", x) // 42    END
    fmt.Printf("%%6.2f (float with width 6, 2 decimals): %6.2f\n", f) //   3.14

    fmt.Printf("\n=== Sprintf Example ===\n")
    formatted := fmt.Sprintf("Hello %s!", s)
    fmt.Println(formatted)
}
```

### Initial Statement of an If Block
```go
// length is only available in the if block scope
if length := getLength(message); length < 1 {
    fmt.Println("message is invalid")
}
```

### Switch

The switch statement in Go is a cleaner way to write multiple if-else conditions (similar to other programming languages).
Have in mind that the `break` statement is not required in Go switch statements, as each case automatically breaks unless you use the `fallthrough` keyword

```go
package main

import "fmt"

func main() {

    // Basic switch example
    day := 3
    switch day {
    case 1:
        fmt.Println("Monday")
    case 2:
        fmt.Println("Tuesday")
    case 3:
        fmt.Println("Wednesday")
    default:
        fmt.Println("Another day")
    }

    // Multiple expressions in one case
    grade := "B"
    switch grade {
    case "A", "B":
        fmt.Println("Good job!")
    case "C":
        fmt.Println("Average.")
    default:
        fmt.Println("Needs improvement.")
    }

    // Switch without expression (like if-else)
    num := 15
    switch {
    case num%3 == 0 && num%5 == 0:
        fmt.Println("FizzBuzz")
    case num%3 == 0:
        fmt.Println("Fizz")
    case num%5 == 0:
        fmt.Println("Buzz")
    default:
        fmt.Println(num)
    }

    // Fallthrough example
    switch num := 5; num {
    case 5:
        fmt.Println("Five")
        fallthrough // forces the next case to execute
    case 6:
        fmt.Println("Six (forced by fallthrough)")
    default:
        fmt.Println("Other")
    }
}
```

### Error Handling

```go
package main

import (
	"errors"
	"fmt"
)

// Function that returns an error
func divide(a, b float64) (float64, error) {
	if b == 0 {
		return 0, errors.New("cannot divide by zero")
	}
	return a / b, nil
}

func main() {
	// Example 1: successful division
	result, err := divide(10, 2)

	if err != nil {
		fmt.Println("Error:", err)
	} else {
		fmt.Println("Result:", result)
	}

	// Example 2: division by zero triggers error
	result, err = divide(10, 0)

	if err != nil {
		fmt.Println("Error:", err)
	} else {
		fmt.Println("Result:", result)
	}
}
```


### Arrays

Arrays are contiguous blocks of memory that store a fixed-size sequence of elements of the same type. They are useful when you know the size of the collection at compile time and want to ensure that the data is stored in a contiguous block for performance reasons.

```go
package main

import "fmt"

func main() {
    var arr [3]int = [3]int{1, 2, 3}
    fmt.Println("Array:", arr)
    fmt.Println("First element:", arr[0])
    arr[1] = 20
    fmt.Println("Modified array:", arr)

    // Slices (dynamic size, backed by arrays - slices are basically arrays with additional functionality)
    // Slices wrap arrays to give a more general, powerful, and convenient interface to sequences of data
    slice := []int{10, 20, 30}
    fmt.Println("Slice:", slice)
    slice = append(slice, 40) // append adds elements
    fmt.Println("Appended Slice:", slice)
    fmt.Println("Slice length:", len(slice))
    fmt.Println("Slice portion:", slice[1:3]) // slicing
}
```

### Maps

Maps are built-in data types in Go that store key-value pairs. They are similar to dictionaries in Python or objects in JavaScript, allowing you to associate values with unique keys for fast retrieval.

If you try to get the value of a key that does not exist in the map, it will return the zero/default value for the value type (e.g., `0` for `int`, `""` for `string`, etc.). You can also check if a key exists in the map by using the two-value assignment form. The two-value assignment form returns the value and a boolean indicating whether the key exists in the map. This is useful to avoid confusion when accessing values that may not be present.

```go
package main

import "fmt"

func main() {
    myMap := map[string]int{
        "apple":  5,
        "banana": 3,
    }
    fmt.Println("Map:", myMap)
    myMap["orange"] = 7 // add new key-value
    fmt.Println("Map after adding orange:", myMap)
    fmt.Println("Value for apple:", myMap["apple"])

    // Check if key exists
    // This is the two-value assignment form
    val, exists := myMap["pear"]
    fmt.Println("Value for pear:", val, "Exists?", exists)
}
```

### Loops

```go
package main

import "fmt"

func main() {
    // For loop (standard)
    fmt.Println("For loop (0 to 4):")
    for i := 0; i < 5; i++ {
        fmt.Println(i)
    }

    // For loop over slice
    fmt.Println("Loop over slice:")
    for index, value := range slice {
        fmt.Printf("Index %d = %d\n", index, value)
    }

    // For loop over map
    fmt.Println("Loop over map:")
    for key, value := range myMap {
        fmt.Printf("Key: %s, Value: %d\n", key, value)
    }

    // Infinite loop (with break)
    count := 0
    for {
        count++
        if count > 3 {
            break
        }
        fmt.Println("Infinite loop count:", count)
    }
}
```

### Strings

Strings in Go are immutable sequences of bytes, typically used to represent text. They are encoded in UTF-8, which allows them to handle a wide range of characters from different languages. Strings can be manipulated using various functions from the `strings` package, such as checking for substrings, converting case, splitting, and replacing parts of the string.

When using `range` on a string, it iterates over the string's runes (Unicode code points), allowing you to correctly handle multi-byte characters. This is important because some characters may be represented by more than one byte in UTF-8 encoding. However, have in mind, that it will skip indexes of multi-byte characters, so if you need to access the byte index, you should convert the string to a rune slice or byte slice first.

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	str := "Hello, 世界"
	fmt.Println("String:", str)
	fmt.Println("Length in bytes:", len(str)) // counts bytes, not runes
	fmt.Println("Contains 'Hello':", strings.Contains(str, "Hello"))
	fmt.Println("To Upper:", strings.ToUpper(str))
	fmt.Println("Split:", strings.Split(str, ","))
	fmt.Println("Replace:", strings.ReplaceAll(str, "Hello", "Hi"))

	// strings.Builder - Efficient string concatenation
  // Use this instead of manually concatenating strings with `+`, especially in loops or when building large strings since this would create a new string each time, leading to performance issues.
	var builder strings.Builder

	builder.WriteString("Hello")
	builder.WriteString(", ")
	builder.WriteString("world!")
	finalString := builder.String()

	fmt.Println("Using strings.Builder:", finalString)

	// You can also write bytes or runes
	builder.Reset() // clears the builder
	builder.WriteRune('👍')
	builder.WriteByte('!')
	fmt.Println("Builder with rune and byte:", builder.String())

	// strings.Join - joining slice of strings
	words := []string{"Go", "is", "fast"}
	joined := strings.Join(words, " ")
	fmt.Println("Joined string:", joined)

	// strings.Repeat - repeat string multiple times
	repeated := strings.Repeat("Na", 4) + " Batman!"
	fmt.Println("Repeated string:", repeated)

	// strings.Fields - split by whitespace
	text := "Go is awesome"
	parts := strings.Fields(text)
	fmt.Println("Fields (split by space):", parts)

	// strings.Trim - removing unwanted characters
	raw := "###clean me###"
	cleaned := strings.Trim(raw, "#")
	fmt.Println("Trimmed string:", cleaned)

	// strconv package for string ↔ number conversion
	// If you're handling numbers in strings:
	// strconv.Itoa(int) → string
	// strconv.Atoi(string) → int
}
```

### Runes

Runes are Go's way of handling Unicode characters. A rune is an alias for `int32`, and it represents a single Unicode code point. This is particularly useful for working with strings that contain non-ASCII characters, as it allows you to correctly handle characters that may be represented by multiple bytes in UTF-8 encoding.

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	runes := []rune(str) // converts string to runes
	fmt.Println("Number of runes (characters):", len(runes))
	for i, r := range runes {
		fmt.Printf("Rune %d: %c (Unicode: %U)\n", i, r, r)
	}

	// Example of modifying string via runes (since strings are immutable)
	// e.g., change 'H' to 'J'
	mutable := []rune(str)
	mutable[0] = 'J'
	newStr := string(mutable)
	fmt.Println("Modified string:", newStr)
```

### Bytes

Bytes in Go are a slice of bytes, which is a sequence of raw binary data. They are often used for low-level data manipulation, file I/O, and network communication. Unlike strings, bytes can be modified, making them suitable for scenarios where you need to manipulate binary data directly.

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	bytes := []byte(str) // converts string to bytes
	fmt.Println("Bytes slice:", bytes)
	fmt.Printf("First byte: %d\n", bytes[0])

	// Converting bytes back to string
	backToString := string(bytes)
	fmt.Println("Back to string:", backToString)
}
```

### Pointers

```go
package main

import "fmt"

func main() {
    x := 10           // Declare an integer variable
    p := &x           // Create a pointer to x

    fmt.Println("x =", x)
    fmt.Println("p =", p)          // p holds the address of x
    fmt.Println("*p =", *p)        // *p dereferences p to get the value of x

    *p = 20                        // Change the value of x through the pointer
    fmt.Println("x after *p = 20:", x)
}

// Output:
// x = 10
// p = 0xc000014090  // (example address, will vary)
// *p = 10
// x after *p = 20: 20
```

- `x` is a regular integer.
- `p := &x` stores the memory address of `x` in `p`.
- `*p` accesses the value at the address `p` points to.
- Changing `*p` updates `x` because they refer to the same memory location.


_Pointers in Functions:_

```go
package main

import "fmt"

// Function using pointer - avoids copying large data
func increment(val *int) {
    *val += 1
}

func main() {
    number := 100
    increment(&number) // Pass address (pointer), no copy
    fmt.Println("Incremented:", number)
}


// Without the pointer, it would look like this:
func increment(val int) int {
    return val + 1
}

func main() {
    number := 100

    // In Go, when you pass a variable to a function by value (which is the default), the function receives a copy of that variable, not the original.
    // It creates a copy of number - val inside the function is a separate copy of the integer value. 
    // Modifying val does not affect number unless you return and reassign it.
    number = increment(number) 

    fmt.Println("Incremented:", number)
}
```

_Why it’s more efficient compared to not using pointers_:
Passing by pointer (*int) avoids copying data, which is especially beneficial with large structs or arrays. The function operates directly on the original value using its memory address, saving memory and processing time compared to making a full copy. This becomes important for large structs or arrays, where copying would be inefficient. Using pointers allows you to modify the original data without the overhead of copying it, leading to better performance and reduced memory usage.


### Slices Contain a Pointer to an Underlying Array

```go
var slice = []int32{1, 2, 3}
var sliceCopy = slice
sliceCopy[2] = 4
fmt.Println(slice)
fmt.Println(sliceCopy)

// Output:
// [1 2 4]
// [1 2 4]
```

- You create a slice with values `[1, 2, 3]`.
- Then you assign `sliceCopy = slice`, which copies the slice header, not the underlying array. Both slice and sliceCopy point to the same backing array in memory.
- When you do `sliceCopy[2] = 4`, you modify the third element of the underlying array.
- As a result, both slice and sliceCopy reflect the change, and when you print both, you get `[1 2 4]`

Thus:
- In Go, slices contain a pointer to an underlying array, a length, and a capacity.
- Assigning one slice to another copies the slice header, not the data, so both variables reference the same data.
- To make an independent copy (deep copy), you need to allocate a new slice and copy the values, e.g.:

```go
sliceCopy := make([]int32, len(slice))
copy(sliceCopy, slice)
```

### Goroutines

```go
package main

import (
    "fmt"
    "sync"
    "time"
)

// Mutex to protect shared access to results slice
var m sync.Mutex

// WaitGroup to wait for all goroutines to finish
var wg sync.WaitGroup

// Simulated database data
var dbData = []string{"id1", "id2", "id3", "id4", "id5"}

// Shared slice to store results
var results = []string{}

func main() {
    start := time.Now() // Record start time

    for i := 0; i < len(dbData); i++ {
        wg.Add(1)              // Increment WaitGroup counter
        go dbCall(i)           // Launch goroutine for each db call
    }

    wg.Wait()                 // Wait for all goroutines to finish
    fmt.Printf("Total execution time: %v\n", time.Since(start))
    fmt.Printf("The results are %v\n", results)
}

func dbCall(i int) {
    defer wg.Done()                        // Mark this goroutine as done on exit
    time.Sleep(2 * time.Second)            // Simulate delay for DB call

    m.Lock()                              // Lock mutex before modifying shared data
    results = append(results, dbData[i])  // Append result safely
    m.Unlock()                            // Unlock mutex
}
```

Besides `sync.Mutex`, there is also `sync.RWMutex`. This allows you to have multiple readers or a single writer at a time. It is useful when you have many read operations and few write operations, as it allows concurrent reads while still ensuring exclusive access for writes. When the `RLock()` is run, it looks up if a full lock (`Lock()`) is still in place, and if so, it waits until the lock is released. If no full lock is in place, it allows multiple readers to access the data concurrently. When a writer calls `Lock()`, it blocks all readers until the write operation is complete. This ensures that the reader only sees data, that is consistent and not being modified by a writer at the same time.


### Channels

Use goroutines without channels when you want to run tasks concurrently but don’t need to share data or coordinate between them. For example, fire-and-forget background jobs where the tasks don’t depend on each other or don’t need to communicate results back.

You need channels when your goroutines must communicate, synchronize, or share data safely. Channels let you pass values between goroutines and coordinate their execution without explicit locks. For instance, if one goroutine produces data and another consumes it, or if you want to wait for a goroutine’s result before continuing, channels are the clean, idiomatic way to do that in Go.

In short:
- Use goroutines alone for independent parallelism without communication.
- Use channels when goroutines need to talk, coordinate, or pass data safely.

Channels help avoid race conditions and make concurrent programs easier to reason about.

#### `select`

In Go, the select statement is like a switch, but for channels. It lets a goroutine wait on multiple channel operations — like sending or receiving — and will execute one case that’s ready. If multiple are ready, one is chosen at random. If none are ready, it blocks (unless there's a default case).

```go
package main

import (
    "fmt"
    "time"
)

// Base example: simple send and receive using an unbuffered channel
func easyExample() {
    ch := make(chan string)        // Create an unbuffered channel of strings

    go func() {
        ch <- "hello from goroutine"  // Send a message into the channel
    }()

    msg := <-ch                    // Receive the message from the channel (blocks until message arrives)
    fmt.Println("Easy example received:", msg)
}

// Advanced example: using a buffered channel with multiple goroutines, select, and closing the channel
func advancedExample() {
    ch := make(chan int, 3)      // Buffered channel
    done := make(chan struct{}) // Channel to signal shutdown

    // Producer: send values into the channel with select
    go func() {
        defer close(ch)
        for i := 1; i <= 10; i++ {
            select {
            case ch <- i:
                fmt.Println("Producer sent:", i)
                time.Sleep(200 * time.Millisecond) // Simulate some delay
            case <-done:
                fmt.Println("Producer received done signal. Stopping.")
                return
            }
        }
    }()

    // Explanation of the select above:
    // The producer wants to send i into the channel ch.
    // But before it just blindly sends, it waits using select:
    // If the channel has space, it sends the value and continues.
    // If the done channel has been closed (from the consumer), it stops early.

    // Consumer: reads from channel and optionally signals done
    go func() {
        timeout := time.After(2 * time.Second) // Set timeout for example

        for {
            select {
            case val, ok := <-ch:
                if !ok {
                    fmt.Println("Consumer: channel closed.")
                    return
                }
                fmt.Println("Consumer received:", val)
                time.Sleep(300 * time.Millisecond) // Simulate processing
            case <-timeout:
                fmt.Println("Consumer timed out. Sending done signal.")
                close(done)
                return
            }
        }
    }()

    // Explanation of the select above:
    // The consumer is waiting to receive from the ch channel.
    // But at the same time, it’s also waiting for a timeout (2 seconds) using time.After.
    // The select waits for whichever happens first:
    // A value arrives on ch: It processes it.
    // The timeout fires: It prints a message, signals the producer to stop (close(done)), and exits.

    // Give enough time for goroutines to complete
    time.Sleep(4 * time.Second)
    fmt.Println("Advanced example with select done.")
}
```

### Generics

```go
package main

import (
    "fmt"
)

// Filter returns a new slice containing only the elements that match the predicate.
func Filter[T any](input []T, predicate func(T) bool) []T {
    var result []T
    for _, val := range input {
        if predicate(val) {
            result = append(result, val)
        }
    }
    return result
}

// Map transforms a slice of type T to a slice of type R using a mapper function.
func Map[T any, R any](input []T, mapper func(T) R) []R {
    result := make([]R, len(input))
    for i, val := range input {
        result[i] = mapper(val)
    }
    return result
}

func main() {
    // Example 1: Filter even numbers from a slice of ints
    nums := []int{1, 2, 3, 4, 5, 6}
    evens := Filter(nums, func(n int) bool {
        return n%2 == 0
    })
    fmt.Println("Even numbers:", evens) // [2 4 6]

    // Example 2: Map ints to strings
    words := Map(nums, func(n int) string {
        return fmt.Sprintf("Number-%d", n)
    })
    fmt.Println("Mapped strings:", words) // ["Number-1", "Number-2", ...]
}
```

### colly & goquery

*Colly*: Colly is a fast and easy-to-use scraping framework for Go. It handles HTTP requests, concurrency, and URL visiting automatically. You define “collectors” for pages, attach callbacks for HTML elements (OnHTML), and Colly manages fetching, retries, and rate-limiting. It’s ideal for scraping static websites where JavaScript rendering isn’t required.

*GoQuery*: GoQuery is a Go library that implements jQuery-like syntax for DOM traversal and manipulation. You can select elements (Find), iterate over them (Each), and inspect child nodes (Contents) or attributes. While GoQuery doesn’t fetch pages itself, it pairs perfectly with Colly or the standard library’s HTTP client for parsing HTML.

When JavaScript is required:
*Chromedp*: Chromedp is a headless Chrome/Chromium controller for Go. Unlike Colly, it can render JavaScript-heavy websites, simulate user interactions, click buttons, and extract dynamic content. It’s more powerful but also heavier and slower than Colly, making it suitable for pages that require a real browser context.

In short: Colly = fast scraping of static pages, GoQuery = DOM parsing and manipulation, Chromedp = full browser automation for dynamic content.

_colly & goquery:_
```go
package main

import (
	"fmt"
	"log"
	"strings"
	"sync"

	"github.com/gocolly/colly"
	"github.com/PuerkitoBio/goquery"
)

type Result struct {
	Link    string
	Title   string
	Content string
}

func ScrapeExample(baseURL string, mu *sync.Mutex, wg *sync.WaitGroup, seen map[string]struct{}, resultsChan chan<- Result) {
	listURL := baseURL + "/articles"

	// List page collector
	cList := colly.NewCollector()

	// Detail page collector
	cDetail := colly.NewCollector()

  	// Apply polite limits
	cDetail.Limit(&colly.LimitRule{
		DomainGlob:  "*example.com*",
		Parallelism: 2,                       // at most 2 requests at the same time
		RandomDelay: 1000 * time.Millisecond, // add a delay between requests
	})


	// Handle detail pages
	cDetail.OnHTML("div.article-content", func(e *colly.HTMLElement) {
		link := e.Request.URL.String()
		contentSelection := e.DOM

		title := strings.TrimSpace(contentSelection.Find("h1").Text())

		// Example: iterate over <p> using Contents() and NodeName
		var combinedText []string
		contentSelection.Contents().Each(func(i int, s *goquery.Selection) {
			nodeName := goquery.NodeName(s)
			text := strings.TrimSpace(s.Text())
			if text != "" {
				combinedText = append(combinedText, fmt.Sprintf("[%s] %s", nodeName, text))
			}
		})

		key := link
		mu.Lock()
		if _, exists := seen[key]; exists {
			mu.Unlock()
			return
		}
		seen[key] = struct{}{}
		mu.Unlock()

		resultsChan <- Result{
			Link:    link,
			Title:   title,
			Content: strings.Join(combinedText, "\n"),
		}
	})

	// Handle list page
	cList.OnHTML("div.article-listing h2.title a", func(e *colly.HTMLElement) {
		link := e.Attr("href")
		wg.Add(1)
		go func(link string) {
			defer wg.Done()
			if err := cDetail.Visit(link); err != nil {
				log.Printf("Failed to visit detail page: %s", err)
			}
		}(link)
	})

	if err := cList.Visit(listURL); err != nil {
		log.Fatal(err)
	}
}

func main() {
	var mu sync.Mutex
	var wg sync.WaitGroup
	seen := make(map[string]struct{})
	results := make(chan Result, 10)

	go func() {
		for r := range results {
			fmt.Printf("Title: %s\nLink: %s\nContent:\n%s\n\n", r.Title, r.Link, r.Content)
		}
	}()

	ScrapeExample("https://example.com", &mu, &wg, seen, results)
	wg.Wait()
	close(results)
}
```

_With chromedp:_
```go
package helper

import (
	"context"
	"time"

	"github.com/chromedp/chromedp"
)

// Use chromedp to open a website and wait for it's html to load in before returning it
// Use "doc, err := goquery.NewDocumentFromReader(strings.NewReader(finalHTML))" to parse it into a goquery reader (to use Find and other methods on it)
func GetFinalHTML(link string) (string, error) {
	ctx, cancel := chromedp.NewContext(context.Background())
	defer cancel()

	var html string
	err := chromedp.Run(ctx,
		chromedp.Navigate(link),
		chromedp.Sleep(2*time.Second), // wait for JS
		chromedp.OuterHTML("html", &html, chromedp.ByQuery),
	)

	if err != nil {
		return "", err
	}

	return html, nil
}
```

### Initial Statement in if block
```go
// something is not exposed to the parent scope
if something := getSomething(name); something < 3 {
    fmt.Println("name is invalid")
}
```

### Type Assertion (https://go.dev/tour/methods/15)

When you write `var a Animal = Dog{}`, the static type of a is Animal (the interface), even though at runtime it holds a Dog; the compiler only knows it’s “some type that implements Animal.” A type assertion like `d, ok := a.(Dog)` is useful because in real programs you often work with interfaces without knowing the concrete type inside (e.g., when processing a list of Animal values that could be Dog, Cat, etc.), so the assertion lets you safely recover the underlying struct if it matches, and ignore or handle it differently if it doesn’t.

```go
    var i interface{} = "hello"

    // Type assertion
    // i.(string) tries to extract the underlying string from the interface{}.
    // The second return value ok is true if the assertion succeeds, false otherwise.
    s, ok := i.(string)
    if ok {
        fmt.Println("String value:", s)
    } else {
        fmt.Println("Not a string")
    }

    // This will fail safely
    n, ok := i.(int)
    if ok {
        fmt.Println("Integer value:", n)
    } else {
        fmt.Println("Not an int")
    }
```

Another example:
```go
// Define an interface
type Shape interface {
	Area() float64
}

// Circle implements Shape
type Circle struct {
	Radius float64
}

func (c Circle) Area() float64 {
	return math.Pi * c.Radius * c.Radius
}

...

var s Shape = Circle{Radius: 5}

// Safe type assertion
circle, ok := s.(Circle)
if ok {
  fmt.Println("Circle radius:", circle.Radius)
  fmt.Println("Circle area:", circle.Area())
} else {
  fmt.Println("Not a Circle")
}
```

### Type Switch (https://go.dev/tour/methods/16)

```go
animals := []Animal{Dog{}, Cat{}, Dog{}}

for _, a := range animals {
  switch v := a.(type) {
  case Dog:
    fmt.Println("Dog says:", v.Speak())
  case Cat:
    fmt.Println("Cat says:", v.Speak())
  default:
    fmt.Println("Unknown animal")
  }
}
```

### Loop Labels

```go
	Outer: // this is the label you can use in an inner loop, for example
	for i := 2; i <= max; i++ {
		if (i % 2 == 0 && i != 2) {
			continue
		}
	
		for j := 2; j * j <= i; j++ {
			if i % j == 0 {
				continue Outer
			}
		}
	
		fmt.Println(i)
	}
```

### Initialize Types
```go
var r rune = 'a'     // rune literal (alias for int32)
i := 42              // int with short declaration
f := 3.14            // float64
s := "hello"         // string
b := true            // bool

var nums []int                 // nil slice
nums = []int{1, 2, 3}          // literal initialization
nums2 := make([]int, 5)        // length 5, filled with zeros
nums3 := make([]int, 0, 10)    // empty slice, capacity 10

arr := [3]int{1, 2, 3}   // fixed length array
arr2 := [...]string{"a", "b", "c"} // length inferred

m := make(map[string]int)        // empty map
m["one"] = 1

m2 := map[rune]string{           // literal initialization
    'a': "apple",
    'b': "banana",
}

ch := make(chan int)     // unbuffered channel
chBuf := make(chan int, 5) // buffered channel (capacity 5)

type Person struct {
    Name string
    Age  int
}

p := Person{"Alice", 30}          // positional
p2 := Person{Name: "Bob"}         // named fields
p3 := &Person{Name: "Charlie"}    // pointer to struct

var ptr *int        // nil pointer
i := 10
ptr = &i            // pointer to int

var x interface{}   // nil, empty interface
x = "hello"         // can hold any type
```

### Error Handling

```go
package main

import (
    "fmt"
    "os"
)

func main() {
    data, err := os.ReadFile("test.txt")

    // There is no special type for an error, and it's also just a string
    if err != nil {
        fmt.Errorf("Error: %w", err)
        return
    }
    fmt.Println("File contents:", string(data))
}
```

### iota (enum-like, but still different)

```go
package main

import (
    "fmt"
)

// ----- 1. Define an "enum" using type + const + iota -----
type Direction int

const (
    North Direction = iota // iota automatically increments: 0, 1, 2, 3
    East
    South
    West
)

// ----- 2. Function to "match" enum-like cases -----
func move(dir Direction) {
    // Go does not have pattern matching like Rust, so we use switch
    switch dir {
    case North:
        fmt.Println("Moving north")
    case East:
        fmt.Println("Moving east")
    case South:
        fmt.Println("Moving south")
    case West:
        fmt.Println("Moving west")
    default:
        // Go enums are just integers, so this default is needed
        fmt.Println("Unknown direction")
    }
}

func main() {
    move(North) // ✅ Moving north
    move(Direction(10)) // ⚠️ Out-of-range, handled by default
}
```

### Goroutine with Channel

```go
package main

import (
	"fmt"
)

// concurrentNumbers launches a goroutine to produce numbers from 1 to n
// and collects them into a slice.
func concurrentNumbers(n int) []int {
	ch := make(chan int) // create a channel to receive numbers
	ans := []int{}       // slice to store results

	// Start a goroutine that sends numbers into the channel
	go func() {
		for i := 1; i <= n; i++ {
			ch <- i // send number to channel (blocks if nobody is receiving)
		}
		close(ch) // signal "no more values"
	}()

	// Receive numbers from the channel until it's closed
	// This loop will block until the goroutine sends something or closes the channel
  // Waits for values from the channel.
  // Appends each value to the slice.
  // Stops automatically when the channel is closed.
	for num := range ch {
		ans = append(ans, num)
	}

	// When the channel is closed, the loop ends and we return the slice
	return ans
}

func main() {
	result := concurrentNumbers(5)
	fmt.Println(result) // Output: [1 2 3 4 5]
}

```

- go launches a goroutine (a lightweight thread).
- ch <- value blocks if no one is ready to receive.
- for range ch blocks until the channel is closed.
- close(ch) is essential to signal the receiver to stop looping.
