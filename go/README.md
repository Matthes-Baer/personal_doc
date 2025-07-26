# Go

## Useful Links
- [Install Go](https://go.dev/doc/install)
- [Learn Go Fast: Full Tutorial](https://www.youtube.com/watch?v=8uiZC0l4Ajw)
- [Boot Dev Tutorial](https://www.boot.dev/lessons/224252be-adc9-452f-8ed0-0b305b25d0cb)
- [Learn Go as JavaScript Developer](https://prateeksurana.me/blog/guide-to-go-for-javascript-developers/?utm_source=tldrwebdev)

## General Information

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

// Advanced example: using a buffered channel with multiple goroutines and closing the channel
func advancedExample() {
    ch := make(chan int, 3)        // Create a buffered channel with capacity 3

    // Producer: send multiple values into the channel
    go func() {
        defer close(ch) // Close channel to signal no more values will be sent

        for i := 1; i <= 5; i++ {
            fmt.Println("Sending:", i)
            ch <- i               // Send i into the channel; blocks if buffer full
        }
    }()

    // Consumer: receive values from the channel until it is closed
    for val := range ch {
        fmt.Println("Received:", val)
        time.Sleep(500 * time.Millisecond)  // Simulate processing delay
    }

    fmt.Println("Advanced example done, channel closed")
}
```
