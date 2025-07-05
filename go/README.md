# Go

## Useful Links
- https://www.boot.dev/lessons/224252be-adc9-452f-8ed0-0b305b25d0cb
- https://prateeksurana.me/blog/guide-to-go-for-javascript-developers/?utm_source=tldrwebdev

## General Information

- Go follows a field after field memory layout for structs. By having a poorly designed order of fields like having a `uint8` type before a `uint16` type - this would lead to Go "align" the `uint16` field, effectively creating some padding (wasted space) to make up for the size difference between the two types; this helps with execution speed but you will have increased memory usage compared with having the proper order of first the `uint16` and then the `uint8` type - [boot.dev lesson on this](https://www.boot.dev/lessons/84de8a08-1f02-47fd-b0a9-cab314162722)
- Summary of What "Not Object-Oriented" Means in Go:
  - No classes: Instead, you have structs and methods.
  - No inheritance: You use composition (embedding structs) to combine behaviors.
  - Interfaces: Used for polymorphism, and they are implicitly satisfied based on method signatures.
  - Simpler model: Focuses on data and behavior with fewer language features to manage.

- The walrus operator, `:=`, declares a new variable and assigns a value to it in one line. It can't be used outside of a function (in the global/package scope).
- Go programs are fairly lightweight. Each program includes a small amount of extra code that’s included in the executable binary called the Go Runtime. One of the purposes of the Go runtime is to clean up unused memory at runtime. It includes a garbage collector that automatically frees up memory that’s no longer in use. 

As a general rule, Java programs use more memory than comparable Go programs. There are several reasons for this, but one of them is that Java uses a virtual machine to interpret bytecode at runtime and typically allocates more on the heap.

On the other hand, Rust and C programs use slightly less memory than Go programs because more control is given to the developer to optimize the memory usage of the program. The Go runtime just handles it for us automatically.
- On of the main purposes of the Go Runtime (which is within each Go executable), is to cleanup unused memory (an automated process)
- Constants can be primitive types like strings, integers, booleans and floats. They can not be more complex types like slices, maps and structs. You cannot declare a constant that can only be computed at run-time like you can in JavaScript. (`time.Now()` would break)
- When you need to work with individual characters in a string, you should use the `rune` type. It breaks strings up into their individual characters, which can be more than one byte long.


## Helpful Methods
- `fmt.Printf()` - Prints a formatted string to standard out (does not automatically end with a newline (\n))
- `fmt.Sprintf()` - Returns the formatted string (does automatically end with a newline (\n))


## Code Examples

### Interfaces

Interfaces are abstract types that define behavior via method signatures, structs on the other hand are concrete data types used to group related fields.

```go
type shape interface {
  area() float64
  perimeter() float64
}

func printShapeData(s shape) {
	fmt.Printf("Area: %v - Perimeter: %v\n", s.area(), s.perimeter())
}
```

### Struct Methods

While Go is not object-oriented, it does support methods that can be defined on structs. Methods are just functions that have a receiver. A receiver is a special parameter that syntactically goes before the name of the function. This way you can basically add methods to structs (compared with classes in OOP languages).

```go
type rect struct {
  width int
  height int
}

// area has a receiver of (r rect)
// rect is the struct
// r is the placeholder
func (r rect) area() int {
  return r.width * r.height
}

var r = rect{
  width: 5,
  height: 10,
}

fmt.Println(r.area())
// prints 50
```

### Embedded Structs

Go is not an object-oriented language. However, embedded structs provide a kind of data-only inheritance that can be useful at times. Keep in mind, Go doesn't support classes or inheritance in the complete sense, but embedded structs are a way to elevate and share fields between struct definitions.

```go
type car struct {
  brand string
  model string
}

type truck struct {
  // "car" is embedded, so the definition of a
  // "truck" now also additionally contains all
  // of the fields of the car struct
  car
  bedSize int
}
```

- Unlike nested structs, an embedded struct's fields are accessed at the top level like normal fields.
- Like nested structs, you assign the promoted fields with the embedded struct in a composite literal.

With the embedded struct type from above, you still create the struct like this (nested car, not on the same level as truck):

```go
lanesTruck := truck{
  bedSize: 10,
  car: car{
    brand: "Toyota",
    model: "Camry",
  },
}

fmt.Println(lanesTruck.brand) // Toyota
fmt.Println(lanesTruck.model) // Camry
```

In the example above you can see that both brand and model are accessible from the top-level, while the nested equivalent to this object would require you to access these fields via a nested car struct: lanesTruck.car.brand or lanesTruck.car.model. If you want to have it nested, you would have to create the struct type like this:

```go
type truck struct {
  car car
  bedSize int
}
```

Thus, `car car` (this would be nested) instead of just `car` (this would be embedded).


### Anonymous Structs

An anonymous struct is just like a normal struct, but it is defined without a name and therefore cannot be referenced elsewhere in the code.

To create an anonymous struct, just instantiate the instance immediately using a second pair of brackets after declaring the type:

```go
myCar := struct {
  brand string
  model string
} {
  brand: "Toyota",
  model: "Camry",
}
```

You can even nest anonymous structs as fields within other structs:

```go
type car struct {
  brand string
  model string
  doors int
  mileage int
  // wheel is a field containing an anonymous struct
  wheel struct {
    radius int
    material string
  }
}
```

Comment from boot.dev instructor on anonymous structs:
"In general, prefer named structs. Named structs make it easier to read and understand your code, and they have the nice side-effect of being reusable. I sometimes use anonymous structs when I know I won't ever need to use a struct again. For example, sometimes I'll use one to create the shape of some JSON data in HTTP handlers.

If a struct is only meant to be used once, then it makes sense to declare it in such a way that developers down the road won’t be tempted to accidentally use it again."

### Structs

We use structs in Go to represent structured data. It's often convenient to group different types of variables together. For example, if we want to represent a car we could do the following:

```go
type car struct {
	brand      string
	model      string
	doors      int
	mileage    int
}
```

This creates a new struct type called car. All cars have a brand, model, doors and mileage.

Structs in Go are often used to represent data that you might use a dictionary or object for in other languages.


### Closures

A closure is a function that references variables from outside its own function body. The function may access and assign to the referenced variables.

In this example, the concatter() function returns a function that has reference to an enclosed doc value. Each successive call to harryPotterAggregator mutates that same doc variable.

```go
func concatter() func(string) string {
	doc := ""
	return func(word string) string {
		doc += word + " "
		return doc
	}
}

func main() {
	harryPotterAggregator := concatter()
	harryPotterAggregator("Mr.")
	harryPotterAggregator("and")
	harryPotterAggregator("Mrs.")
	harryPotterAggregator("Dursley")
	harryPotterAggregator("of")
	harryPotterAggregator("number")
	harryPotterAggregator("four,")
	harryPotterAggregator("Privet")

	fmt.Println(harryPotterAggregator("Drive"))
	// Mr. and Mrs. Dursley of number four, Privet Drive
}
```

### Defer

The defer keyword is a fairly unique feature of Go. It allows a function to be executed automatically just before its enclosing function returns. The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding function returns.

Deferred functions are typically used to clean up resources that are no longer being used. Often to close database connections, file handlers and the like.

For example:

```go
func GetUsername(dstName, srcName string) (username string, err error) {
	// Open a connection to a database
	conn, _ := db.Open(srcName)

	// Close the connection *anywhere* the GetUsername function returns
	defer conn.Close()

	username, err = db.FetchUser()
	if err != nil {
		// The defer statement is auto-executed if we return here
		return "", err
	}

	// The defer statement is auto-executed if we return here
	return username, nil
}
```

In the above example, the `conn.Close()` function is not called here:

```go
defer conn.Close()
```

It's called:

```go
// here
return "", err
// or here
return username, nil
```

Depending on whether the GetUsername function errored.

Defer is a great way to make sure that something happens before a function exits, even if there are multiple return statements, a common occurrence in Go.


### Named Return Values / Naked Returns

```go
func getCoords() (x, y int){
  // x and y are initialized with zero values

  return // automatically returns x and y
}
```

Is the same as (this would be a naked return, instead of a named return):

```go
func getCoords() (int, int){
  var x int
  var y int
  return x, y
}
```

Thus, you can do stuff like this:

```go
func yearsUntilEvents(age int) (yearsUntilAdult, yearsUntilDrinking, yearsUntilCarRental int) {
	yearsUntilAdult = 18 - age
	if yearsUntilAdult < 0 {
		yearsUntilAdult = 0
	}
	yearsUntilDrinking = 21 - age
	if yearsUntilDrinking < 0 {
		yearsUntilDrinking = 0
	}
	yearsUntilCarRental = 25 - age
	if yearsUntilCarRental < 0 {
		yearsUntilCarRental = 0
	}
	return
}
```

Within the function signature you already tell which variables are initialized and returned (named return values). Within the function's body you use the same variables to set their values. With just `return` you return them in the order of the function's signature. 

You may also explicitly overwrite the return values defined in the function's signature:

```go
func getCoords() (x, y int){
  return 5, 6 // this is explicit, x and y are NOT returned
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

// %t for booleans
s := fmt.Sprintf("Is friendly: %t", false)
// Is friendly: false
```

### Initial Statement of an If Block
```go
// length is only available in the if block scope
if length := getLength(email); length < 1 {
    fmt.Println("Email is invalid")
}
```

### Switch

In Go, the break statement is not required at the end of a case to stop it from falling through to the next case. The break statement is implicit in Go.

```go
func getCreator(os string) string {
    var creator string
    switch os {
    case "linux":
        creator = "Linus Torvalds"
    case "windows":
        creator = "Bill Gates"

    // all three of these cases will set creator to "A Steve"
    case "macOS":
        fallthrough
    case "Mac OS X":
        fallthrough
    case "mac":
        creator = "A Steve"

    default:
        creator = "Unknown"
    }
    return creator
}
```

