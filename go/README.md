# Go

## Useful Links
- [Install Go](https://go.dev/doc/install)
- [Learn Go Fast: Full Tutorial](https://www.youtube.com/watch?v=8uiZC0l4Ajw)
- [Boot Dev Tutorial](https://www.boot.dev/lessons/224252be-adc9-452f-8ed0-0b305b25d0cb)
- [Learn Go as JavaScript Developer](https://prateeksurana.me/blog/guide-to-go-for-javascript-developers/?utm_source=tldrwebdev)

## General Information

- Go is a Statically Typed Language: This means that the type of a variable is known at compile time, and you must declare the type of a variable when you create it. This is different from dynamically typed languages like JavaScript, where types are determined at runtime.

- Go is a Strongly Typed Language: This means that you cannot perform operations on variables of different types without explicitly converting them. For example, you cannot add a string and an integer together without converting one of them to the other's type.

- Go code is compiled into machine code, which makes it fast and efficient. This is different from interpreted languages like JavaScript, where the code is executed line by line at runtime.

- Go has fast compilation times, which means that you can quickly build and run your code without waiting for long periods.

- Go has built in concurrency support, which allows you to write programs that can run multiple tasks simultaneously. This is achieved through goroutines and channels, which are lightweight threads and communication mechanisms in Go.

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
-  Prints the type of variable: `fmt.Printf("%T\n", someVar)`

## Code Examples

### Interfaces

Interfaces are abstract types that define behavior via method signatures, structs on the other hand are concrete data types used to group related fields.

```go
package main

import "fmt"

// Define an interface
type Shape interface {
    Area() float64
    Perimeter() float64
}

// Define a struct - Rectangle
type Rectangle struct {
    Width, Height float64
}

// Implement the Shape interface for Rectangle
func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}

func (r Rectangle) Perimeter() float64 {
    return 2 * (r.Width + r.Height)
}

// Define another struct - Circle
type Circle struct {
    Radius float64
}

// Implement the Shape interface for Circle
func (c Circle) Area() float64 {
    return 3.1415 * c.Radius * c.Radius
}

func (c Circle) Perimeter() float64 {
    return 2 * 3.1415 * c.Radius
}

// Main function
func main() {
    var s Shape

    s = Rectangle{Width: 10, Height: 5}
    fmt.Println("Rectangle Area:", s.Area())
    fmt.Println("Rectangle Perimeter:", s.Perimeter())

    s = Circle{Radius: 7}
    fmt.Println("Circle Area:", s.Area())
    fmt.Println("Circle Perimeter:", s.Perimeter())
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
