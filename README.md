<p align="center">
  <img src="https://github.com/TotallyNotAHaxxer/MartianDefense-Golang-MDFiles/blob/main/ycQqVry.png">
</p>

# Module (Go) introduction

This module within the Martian Defense gitbook goes over the Go programming language. The Go programming language is used quite often in the cyber security world and is much more worth it to learn than you might think. For context, Go is a statically typed, machine code compiled and versatile programming language that can be used for many security specific tasks such as reverse shells, cryptography, networking, server side and client side development and even malware development.

# Sub Page -> Go | For Security 

Golang is a programming language that has many amazing features to it, so what exactly makes go suited for security specifically? In order to solve this, a table has been provided below.

| Feature | Reason for use in cyber security |
| ------- | -------------------------------- |
| Standard Library | Most language's currently used in cyber security realms that are interpreted such as python have a major issue with not providing the correct standard library to do exactly what you need. this leaves it completely up to the user to download and install third party libraries to complete the task they need to. Golang has an amazing standard library that makes it easy to setup requests, parse files, load specific information while also allowing for a much more versatile impact | 
| Type System | Unlike most programming language's, go has an amazing type system which holds data types such as rune, string, interface, byte, unsigned integers, big integers, integers, floats, complex numbers and even more mathematically detailed data types. This allows users to easily work with files, systems and type specific operations |
| Speed and performance | Golang is one of the faster more used programming language's because of the way it's compiler optimizes and generates code while also working with virtual tables! |
| Concurrency | Another amazing feature of the Go programming language is that it is a very very thread heavy language and has support for atomic, async, mutex and other various threading factors |

# Sub Page -> Go | Introduction

Golang is a interesting programming language and has a weird syntax, so lets explain the rules of the compiler before we jump into everything.

## Sub Page -> Golang | Files ##

Every programming language has some form of file system, it has some form of extension that is also run through the compiler or interpreter. Golang has multiple files which are placed in the table below.

| File type / Extension | Purpose or reason for use |
| --------------------- | ------------------------- |
| .go                   | Golang source code file. These types of files are where source code will come into handy |
| .mod                  | Golang Module file. These files are used for directories and module development which will be talked about later |
| .sum                  | Golang Module file which holds all the cryptographic signatures for third party libraries in use within the project |

## Sub Page -> Golang | Entry Points ##

Like most compiled and statically typed lamguages such as C, C++, Assembler, Fortran etc Golang has a main entry point and a sub entry point that is optional. What do I mean when I say sub entry point and main entry point. The main entry point of a golang program is defined as `main` while a sub entry point is called `init`. These are both possible entry points that can be placed wherever in the file.

### The `init` sub entry point###

Golang has a weird file layout which we will go over in a second, but for now lets go over the entry points. The first entry point we are going over is the optional entry point. This function is defined like so.

```go
func init() {
    // Golang code here
}
```

The init function and entry point can be defined in multiple places throughout the entire source code file or project solution. In this case, an initation function or sub entry point is a function that is typically used for initation of a program. This means that whatever is under the `init` function will run before main. So, we can build a program to do a small mathematical operation and print it to the screen.

```go
func init() {
  println(2 + 20) // Output: 22
}
```

and this will then be run before main. This entry point is not a primary entry point for go and can not be used as a final entry point to the program, so we need to use `main`

### The `main` entry point ###

This is the actual program entry point within the program, this MUST be declared for a go program to run. To declare a main function we can do it as shown below.

```go
func main() {
    // main code and calls here
}
```

and when we run our program it will execute. 

### Clashing with init and main | Rules ###

INIT functions CAN NOT BE CALLED. This is because the go compiler will prioritize these calls on the backend already and double calling an initation function is not directly supported or should be done anyway. 

Below is a list of rules for init and main functions 

> `init` or `main` functions can NOT be called by the user 
> In order to use a `init` function `main` must be declared
> `init` functions can be declared in any source code file 
> `main` functions have to be placed in a .go source code file with the package of `main`

# Module (Go Theory) | Intro

Go has a different syntax and is kinda confusing for some people to get around so this module will be discussing theory within the Go programming language.

> What is programatic theory?

When it comes to programming, theory, is the study of concepts within a program or in this case specific programming language. Learning theory will help you learn the logical pathways for the language and understand how to piece new concepts together.

> What will this module contain?

This this is not CompSCI, Programatic, General or computational theory and rather a field that focuses on the prime aspects; This module will contain information about the Go programming language such as a file layout, module layout, type system, working with different structures, working with functions and so on from there.

## Sub Page -> Go Theory | File Contruction

When it comes to working with Go, there are many missed aspects within the language, such as the file construction. Within golang, there are is multiple fields to talk about, the top level, mid level and bottom level of the program. Typically, the mid of the file is the secondary "top" level of the program. What defines these?

> Top Level

The top level of a go program or .go source code file MUST contain a package name. To declare a package name you type `package` followed by the name of the package or module you are making. For the basic sense of things, a simple go program that is a main file or main entry to a program, must contain `package main` this is also where the `main` entry point is to the program.

```go
package main 

func main() {
    println("hi")
}
```

This is pretty simple to understand as the first and primary top level of the program or first line of every go program MUST contain a package name.

> Secondary Top Level AKA Mid level.

For programs that use libraries, Golang only allows you to import or link modules using the import keywords for which is defined at the top of a program. Say we want to write " hey guys \n hows it going! " in a program using the FMT package. We have to write this in the following form 

```go
package main 

import "fmt"

func main() {
  fmt.Print("hey guys! \n hows it going!")
}
```

This is pretty easy to dissect and look at, what about listed imports? Cool thing about go is that importing files or even libraries or modules can all be done simply by using a list within the import expression which is shown below.

```go
package main

import (
    "fmt"
    "os"
)

func main() {
  fmt.Println(os.Args[1])
}
```

This program prints out the arguments when the program is run or rather the first command line argument. As you can see, the import list does not require comma's as it relies on whitespace.

> Bottom Level 

The bottom level of a program is where all your functions are typically going to be stored or executed calls. In the case of our program above, the main function is at the bottom level or scope of the program.

## Sub Page -> Go Theory | Executing Files 

> Basic execution

Executing golang source code files can be quite easy, but golang has quite the tools. To simply run a golang file such as the one shown below 

```go
package main 

func main() {
    println("hi")
}
```
 
you type `go run main.go`. Remember that the main file must have `package main` in order for it to be run and have a valid entry point declared as `main` for the program to run.

> Building to a executeable

In order to build a golang program for the current architecture or system you are on, simply run `go build`. When this is built if no output flag is defined, golang will then take the file name and compile it to have the executeable name set as the file names. So if we compiled `hello.go` without a specification on the name then the output will be `hello.exe` on windows or `hello` on linux.

> Naming builds 

Golang has many variables and flags you can use to optimize the build's name and target. 

Use the `-o` option followed by a name to compile by name like so; `go build -o HelloProgram main.go`

> Using Env variables to customize builds and targets

In the previous section I had mentioned environment variables and types for the Go programming language. Well, Go has the following environment variables.

| Environment Variable | Description                                                | Example                              |
|----------------------|------------------------------------------------------------|--------------------------------------|
| `PATH`               | Specifies directories to search for executable programs     | `/usr/local/bin:/usr/bin:/bin`        |
| `HOME`               | Specifies the user's home directory                         | `/Users/username`                    |
| `USER`               | Specifies the username of the current user                  | `johndoe`                            |
| `GOPATH`             | Specifies the Go workspace directory                        | `/Users/username/go`                  |
| `GOROOT`             | Specifies the directory where the Go installation is located| `/usr/local/go`                      |
| `GOOS`               | Specifies the target operating system for the build         | `linux`                              |
| `GOARCH`             | Specifies the target architecture for the build             | `amd64`                              |
| `GOBIN`              | Specifies the directory where Go binaries should be installed| `/Users/username/go/bin`              |
| `GOENV`              | Specifies the path to a file that overrides environment vars| `/Users/username/.go/environment`     |

In order to use these environment variables we can change their values before build such as 

`GOOS=linux go build -o hello main.go`

which will build the file specific towards the ELF file format.

> Looking for environmental support

Sometimes when working with Go and compiling programs in Go, you may want to compile for another architecture and system. To do so, execute the following command to drop a list of all architectures and operating systems supported.

`go tool dist list`

which will drop down the entire list of possible targets allows by the compiler.

We can now make our program build for AMD64 and Linux by issuing the following command

```
GOOS=linux GOARCH=amd64 go build -o main main.go
```


## Sub Page -> Go Theory | Functions

Before we get into the data types of Golang we want to first be able to understand how functions work. This module will be aimed at giving you a base introduction to functions and then an intermediate example of those functions.

> Functions | Basic Function Decl

In order to declare functions in Golang there are multiple ways you can initalize them and even declare them, but the main one is the `func` keyword which stands for `function` similar to `fn` in rust.

Below is an example of a very basic function and how you can call them.

```go
package main 

import "fmt"

func HelloWorld() {
	fmt.Println("hello world")
}

func main() {
	HelloWorld()
}
```

This function is declared and takes no arguments, returns nothing and has no structure tag as it simply just prints hello world to the console. Now, if we wanted to go bigger we could. Lets look at the anatomy of a function in Go.

> Functions | Anatomy of a function

A function has an few interesting fields but the prime exist of all optional sets.

```go
func     ()      FuncName  		()	     space or ()  {}
|         |          |			 |		|	   |
| Decl    |          | 			 |		|	   |
          |          | ----------	 |		|	   |
	  Optional Struct Tags	 |----Param List	|	   |
	                         |		   return list	   |
			Function Name				   |Block statement

// Assembled function anatomy

func ()FuncName()(){}
```

Still confusing? Lets break this down then.

**Function Decl**: We established that declaring a function in go requires the `func` keyword

**Function Type Tags**: In golang, you can use type alliases or structures to call a function ( explanation on this later ). This is defined with () before the function name

**Function Name**: Function name comes after the `func` keywords if structure tags or type tags are not within the function

**Function Params / Arguments**: Functions in golang can have arguments and you declare this by delcaring the function name then a set of parenthesis

**Function Returns**: Function return types in go can be declared multiple ways. If you want to declare a list of return types then you have to use () which is the list of types like `(string, int, string)` or you can just declare the type after the function parameter decl.

**Function Block**: Function blocks are called and defined with right and left facing brackets. Right facing brackets define the functions start and left facing brackets define the end of a function.

> Functions | Arguments 

A function as shown above can have multiple arguments, but how do you define them?

Functions have a few rules when types are used as arguments which are the following.

| Rule | Description | Example |
| ---- | ----------- | ------- |
| Any Type | Functions can hold ANY data type | func setting(a string, b map[string]string, c []byte, d interface{}){} |
| Main can not hold function arguments | any `main` function can not hold any parameter or argument and return nothing | main(data string) is ILLEGAL |
| params must be named | for each argument within a function it must be named | func setting(age int, name string) |  

Arguments as you can see are quite simple and basic despite having some rules, lets write a program demoing how function arguments can be used

```go
package main

import "fmt"

func Hello(name string) {
	message := "Hello there " + name
	fmt.Println(message)
}

func main() {
	Hello("ryan")
}
```

When this program outputs we get `hello there ryan` because we used the string argument "ryan" as a replacement for name and concentrated the strings together. Note that arguments can also be defined in many different ways as well such as infinite arguments otherwise known as vardaic functions.

Lets build a program that allows you to output one giant line of concentrated strings

```go
package main

import "fmt"

func Hello(name ...string) {
	var message string
	for i := 0; i < len(name); i++ {
		message += name[i] + " ,"
	}
	fmt.Println(" hello there! " + message)
}

func main() {
	Hello("ryan", "jef", "dom", "json", "alex")
}
```

Running this code will produce a output that will concentrate all the names provided in the argument list. Note that infinite arguments MUST ALWAYS BE DEFINED AT THE END. So for example the function `func hi(name ...string, age int)` will throw the error `can only use ... with final parameter in list, COMPILER ERROR > MisplacedDotDotDot`

> Functions | Multiple variables at once in arguments

Functions can also use multiple variables all of one type within functions like the following.

```go
func Hello(name, rank string) {}
```

both `name` and `rank` all have to be string types when the function is called, but instead of doing `name string, rank string, player string, user string` you can concentrate that into a list of variables with one assigned type.

> Functions | Returns

Returns are quite simple, the most basic return of a function happens outside of its parameter list and is defined by the data type you want to return. The function below returns an integer data type after adding two parameters.

```go
package main

func Add(x, y int) int {
	return x + y
}

func main() {
	res := Add(10, 20)
	println(res)
}
```

The function takes not only two input params of type integer but then returns the result by adding them together. In our main function we just declare a variable to hold the result of that function and then print it to the console.

> Functions | Returns (Variable and List based)

Functions can also return multiple types and even declare variables like the following function below which returns two variables of the same type

```go
package main

func Add(x, y int) (res, ogval1, ogval2 int) {
	ogval1 = x
	ogval2 = y
	res = x + y
	return
}

func main() {
	res, og1, og2 := Add(10, 20)
	println(res, og1, og2)
}
```

When you return variables within a function, you do not need to return direct values or variables as using the `return` keyword will just return the variables. Looking back at the anatomy, the secodn set of parenthesis is the listed or variable return set. We can also just return multiple types without having variables like so.

```go
package main

func Add(x, y int) (int, int, int) {
	ogval1 := x
	ogval2 := y
	res := x + y
	return res, ogval1, ogval2
}

func main() {
	res, og1, og2 := Add(10, 20)
	println(res, og1, og2)
}
```

Notice that this time we have to declare the variables with the decl operator `:=` and specify them within the return call. If you are working with more bigger functions that return larger sets of data, declaring a list of variables and types may become much more helpful. 

> Functions | Anonymous functions

Functions in Go can be defined using the func() keyword, and we call them typically by the name of the function. But what about anonymous functions? How do those work? What can we do with them?

Anonymous functions are functions that have no name and are called directly. This means we define func() and then call it. A program below defines the use of this.

```go
package main

import "fmt"

func Add(x, y int) {
	fmt.Println(
		fmt.Sprint(x) +
			" + " +
			fmt.Sprint(y) +
			" = " +
			fmt.Sprint(x+y),
	)
	// Now call divide
	func(x1, y1 int) {
		fmt.Println(
			fmt.Sprint(x) +
				" / " +
				fmt.Sprint(y) +
				" = " +
				fmt.Sprint(x1/y1),
		)
	}(x, y)
}

func main() {
	Add(12, 20)
}
```

This is an example of what a anonymous function looks like. The function defined is `Add` which takes two parameters of type int, it then formats the output of the calculation. Lets break this section down line by line.

```go
	fmt.Println(
		fmt.Sprint(x) +
			" + " +
			fmt.Sprint(y) +
			" = " +
			fmt.Sprint(x+y),
	)
	// Now call divide
```

In this part of the brick all we are doing is a simple `x + y` operation where we add the input values and we print it to the screen. We do this by making an operation called `Sprint` which stands for `String` print to convert any data type to a string. We then concentrate the result of `Sprint(x)` with `+` to format the expression, then add the sprint of y, then an assignment operator and the final result being the operation that was sprinted. So out final message should look like `12 + 20 = 32`

```go
	// Now call divide
	func(x1, y1 int) {
		fmt.Println(
			fmt.Sprint(x) +
				" / " +
				fmt.Sprint(y) +
				" = " +
				fmt.Sprint(x1/y1),
		)
	}(x, y)
```

This brick calls the anonymous function, anonymous functions have a way of calling and returning data types but in this case we just call it with arguments ot simulate a more advanced scenario. Generally speaking we call an anonymous function by using `func(){}()` where the first set of `()` is the param list the function takes and the second set of `()` is the argument input. We then do the same exact operation that we did before this block of code just for division. 

Now lets look at a much more basic function that just outputs a hello world statement.

```go
func(){
	println("hello world")
}()
```

ah yes this is more readable and should give you a good understanding of what exactly a anonymous function looks like in go.




 
## Sub Page -> Go Theory | Data Type System

Golang has a very strong type system that allows you to do so much such as creating your own type structures but before we get into that we should define all of the data types and get a simple understanding of every data type.

| Data Type   | Description                                   | Example                    | Use Case                                                     |
|-------------|-----------------------------------------------|----------------------------|--------------------------------------------------------------|
| `bool`      | Boolean type representing true or false values | `true`, `false`            | Storing and manipulating logical conditions                  |
| `int`       | Signed integer type                           | `42`, `-10`, `0`           | Representing whole numbers                                   |
| `int8`      | 8-bit signed integer type                     | `-128`, `127`              | Optimizing memory usage for smaller integer values           |
| `int16`     | 16-bit signed integer type                    | `-32768`, `32767`          | Handling larger integer values                               |
| `int32`     | 32-bit signed integer type                    | `-2147483648`, `2147483647`| Interacting with system calls, networking, and file systems  |
| `int64`     | 64-bit signed integer type                    | `-9223372036854775808`, `9223372036854775807`| Dealing with very large integer values        |
| `uint`      | Unsigned integer type                         | `0`, `255`, `1000`         | Representing positive whole numbers                          |
| `uint8`     | 8-bit unsigned integer type                   | `0`, `255`                 | Manipulating bytes and color values                           |
| `uint16`    | 16-bit unsigned integer type                  | `0`, `65535`               | Managing network protocols and encoding                      |
| `uint32`    | 32-bit unsigned integer type                  | `0`, `4294967295`          | Working with large sets of unique identifiers                 |
| `uint64`    | 64-bit unsigned integer type                  | `0`, `18446744073709551615`| Handling large numbers or bit manipulation                   |
| `float32`   | Single-precision floating-point type          | `3.14`, `-1.23e-5`         | Representing and manipulating decimal numbers with less precision  |
| `float64`   | Double-precision floating-point type          | `3.14159`, `-1.23456e-10`  | Handling decimal numbers with higher precision               |
| `string`    | Sequence of characters                        | `"Hello, world!"`, `""`     | Storing and manipulating text                                |
| `array`     | Fixed-size collection of elements              | `[1, 2, 3]`, `["apple", "banana", "cherry"]`| Working with a fixed number of related values |
| `rune`      | Unicode code point                             | `'A'`, `'\u03A3'`          | Working with individual characters and Unicode strings       |
| `byte`      | Alias for `uint8`, represents a single byte    | `0x41`, `255`              | Handling binary data, I/O operations, and network protocols  |


All of these data types seem quite confusing but this can be quite easy to understand when we get a short hang of everything.

> Arrays 

Arrays are a very powerful data type within Go and can be used for many different things. Arrays are weird syntactically within Go but can be easy to remember. The following  sub list talks about different arrays and their use case.

**String Arrays**

String arrays can be defined with `[]string`. Generally speaking, all arrays within the go programming language are declared with `[]<type>` where `<type>` is replaced with the data type from the table above.

String arrays look like the following.

```go
var StrArr = []string{
	"hello world1",
	"hello world2",
	"hello world3",
	"hello world4",
}
```

**Float Arrays**

Float arrays follow the same concept

```go
var FloatArr = []float64{
	1.9909999,
	234.9909999,
	34.9909999,
	3423523.9909999,
}
```

**Integer Arrays**

Like all arrays integer arrays are the same 

```go
var IntArr = []int{
	1,
	2,
	3,
	4,
	5,
}
```

> The interface data type

The interface data type is the `any` data type of the Go programming language. This means that this data type can be anything and can be one data type of any type within the type list in Go. Interfaces are defined with `interface{}` and have their own unique fields. Below is an example of a interface array.

```go
var InterfaceArray = []interface{}{
	"hello world",
	1,
	true,
	false,
	[]string{"hi!"},
}

```

Notice how the array does not have any one specific type? That is how an interface works, it is any possible data type.

> The rune data type 

Runes are another confusing factor with people, for some reason it can be confusing to chomp down so lets break it down. A rune is golang's way of declaring unicdoe point. The following example prints out `65`.

```go
func main() {
	r := rune('A')
	println(r)
}
```

This program outputs the value of r, but if r is a character then why is it outputting `65`? This is because A as a unicode point holds the 65th position on the ASCII table shown below.

<p align="center">
  <img src="https://github.com/TotallyNotAHaxxer/MartianDefense-Golang-MDFiles/blob/main/asciifull.gif">
</p>

As you can see rune is just another way to represent unicode point. Note that the rune type can only be used for single characters and can not be more than one character or one unicode point.

> The byte type 

The byte type witin the programming language is easy to understand and does not have a weird understanding behind it. Bytes come in two forms which include a standard byte and a range of bytes ( array of bytes ). Below is an example of both

```go
package main

import "fmt"

var ShellCode = []byte{
	0x90, 0x90, 0x90, // Example shellcode bytes
}

func main() {
	fmt.Println(string(ShellCode))
	r := byte('h')
	println(r)
}
```

As you can see the byte type can be used for many things and if we print the h character in a byte format we get `104` similar to when we work with rune. Using byte's can be super benifical when reading files, working with networks, dissecting packets or trying to parse binary data and files.

## Sub Page -> Go Theory | Type 

The type system we just went over but did not fully cover, one thing we missed was the type and struct keywords. In Golang, you can create your own data types using the type keyword and also create your own data type structures ussing the struct keyword. There are multiple ways to work with this but lets first break down the type keyword.

> `type` basic usage | Type Aliases

The type keyword allows you to create alliases to other data types which can be used to shorten the lenght of specific functions, uses, cases or even arguments. Below is an example 

```go
type UserID int
type Username string

func main() {
    id := UserID(42)
    username := Username("john_doe")
    fmt.Println(id)      
    fmt.Println(username) 
}
```

As you can see we made UserID of type int which means we can now use it and call it as a type.

> `type` different usage | New Data Types 

Creating new data types can also be helpful especially when you want to work with functions or even hold sets of data. In this case we create a Celsius and Fahrenheit data type which are both float64 values.

```go
type Celsius float64
type Fahrenheit float64

func (c Celsius) ToFahrenheit() Fahrenheit {
	return Fahrenheit(c*9/5 + 32)
}

func main() {
	cel := Celsius(25)
	f := cel.ToFahrenheit()
	fmt.Println(f) // Output: 77
}
```

We declare our types using the type keyword, their name followed by the type and then define a function that requires the Celsius type to be called which causes a function to output the Fahrenheit data type. This type of usage for types really comes in handy when we get to better and more detailed operations. It is quite simple to read the code if you are not directly new to go but can be confusing for new comers so lets break it down one last time.

**Types:** We declare the types we want to use using the `type` keyword we then define the data type that new data type we are creating is holding.

**Function Call**: The function in this program converts celsius to fahrenheit and in order to do that the function needs to use the Celsius data type. After the `func` keyword is defined, we place a set of parenthesis which holds the variable we will use to call the structure and then the structure name. We then declare the function name and what it is returning and return the Fahrenheit conversion algorithm with the variable `c` which again is the Celsius type which holds a float64 data type.

**Main**: Our main function is the main entry point that will call the Celsius type to iniate a new value for `cel`, we then call `f` the output to the function by calling `cel.ToFahrenheit()`. 

## Sub Page -> Go Theory | Struct 

Structures are an amazing composite data type that allows you to define your own custom data structure. This can become helpful when building programs in Golang because it allows for developers to easily define custom data types and organize related data. 

> `Struct` | Theory

Structures can be easily declared with the type and struct keywords! The anatomy of the structure is the following

```go		
					 		  | <- Expression
type      StructName       struct			 { }
|	  | 			|			 | |
|	  |			|			 | | 
|	  |__			|			 | |
|	    | Structure Name	|			 | |__structure END____
| Type initalization		| Struct decl		 |___structure START__|
```

so putting a structure together we have 

```go
type StructName struct {
	// Expressions
}
```

> `Struct` | Basic Usage

Using a structure for most people is quite easy when you get the hang of it! The following program uses a structure to store a username and password

```go
package main

import "fmt"

type Config struct {
	Name     string
	Password int
}

var Conf Config

func init() {
	Conf.Name = "Username"
	Conf.Password = 334234
}

func main() {
	fmt.Println("Username ( " + Conf.Name + " ) is password: " + fmt.Sprint(Conf.Password))
}
```

As you can see, this program first starts off by declaring the structure and two variables; `Name of type String` and `Password of type Integer`. When the structure is declared we then see the `var Conf Config` which may be easy to pick apart but in case not, the `Conf` variable holds the Struct `Config` as a value. This is the variable we will use to globally work with the structure. We then create a pre entry point in the program where we can assign the structure variables and then the main function will print out the details.

> `Struct` | Initializing Structs

When we do not want to using variables, we can initialize structures using basic variables like so.

```go
package main

import "fmt"

type Config struct {
	Name     string
	Password int
}

func main() {
	p := Config{
		Name:     "Username",
		Password: 2534334,
	}
	fmt.Println("Username: ( " + p.Name + " ) has password: " + fmt.Sprint(p.Password))
}
```

Sometimes this can come in handy when we want to use structures under specific functions instead of just globally initializing them!

> `Struct` | Anonymous structures

Anonymous structures are quite easy to understand as they provide much more flexibility for their use case and work similar to anonymous functions!

```go
package main

import "fmt"

func main() {
	p := struct {
		Username string
		Password int
	}{
		"Dave",
		1233,
	}
	fmt.Println(p.Password)
	fmt.Println(p.Username)
}
```

As you can see by the initializing it can go quite the long way when you need a structure quick and easy for private use!

> `Struct` | Pointer to Struct

Sometimes, a function may require a structure as an argument and in order to do that we need to be sure that we can work with different structures! A program below takes a structure as a pointer and assigns new values to that structure.

```go
package main

import "fmt"

type Person struct {
	Name string
	Age  int
}

func UpdateUsers(p *Person, name string, age int) {
	p.Name = name
	p.Age = age
}

func main() {
	p := &Person{
		Name: "John Doe",
		Age:  30,
	}

	fmt.Println("\nBefore update:")
	fmt.Println("\tName:", p.Name)
	fmt.Println("\tAge:", p.Age)

	UpdateUsers(p, "Jane Smith", 25)

	fmt.Println("\nAfter update:")
	fmt.Println("\tName:", p.Name)
	fmt.Println("\tAge:", p.Age)
}
```

In this program, we define a `Person` struct with `Name` and `Age` fields. The `UpdateUsers` function takes a pointer to a `Person` struct as an argument, along with new values for the name and age. Inside the function, we use the pointer to update the values of the structure fields. Then in the `main` function, we create a new instance of `Person` using the address-of operator (`&`) (The address-of operator in Go is represented by the & symbol. It is used to obtain the memory address of a variable or a value. ). We then print the initial values of the structure fields. Next, we call the `updatePerson` function, passing the pointer to the `Person` instance and new values. The function modifies the structure fields using the pointer. Finally, we print the updated values of the structure fields.

> `Struct` | Structure Composition

When working with structs in Go, you may want to use one structure that holds a variable with the value of another structure. This looks like the following.

```go
package main

import "fmt"

type Address struct {
	Street  string
	City    string
	Country string
}

type Person struct {
	Name    string
	Age     int
	Address Address
}

func main() {
	address := Address{
		Street:  "123 Main Street",
		City:    "Cityville",
		Country: "Countryland",
	}
	person := Person{
		Name:    "John Doe",
		Age:     30,
		Address: address,
	}

	fmt.Println("Name:", person.Name)
	fmt.Println("\nInfo \tAge:", person.Age)
	fmt.Println("\tAddress:")
	fmt.Println("\tStreet:", person.Address.Street)
	fmt.Println("\tCity:", person.Address.City)
	fmt.Println("\tCountry:", person.Address.Country)
}
```

As you can see we create multiple variables that hold the structurs storing the data we need it to store, notice how when we get to the `Address` field in the variable `person` we fill the `Address` field with the `address` variable that holds a structure and its values apart of the `Address`.

> `Struct` | Structure Tags

Another use for structures is to take forms of data such as JSON, XML, YAML and using it to store those values which can be marshaled into the data structure.

```go
package main

import (
	"encoding/json"
	"fmt"
	"log"
)

type Person struct {
	Name  string `json:"name"`
	Age   int    `json:"age"`
	Email string `json:"email,omitempty"`
}

func main() {
	person := Person{
		Name:  "John Doe",
		Age:   30,
		Email: "johndoe@example.com",
	}

	jsonData, err := json.Marshal(person)
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(string(jsonData))
}
```

This is quite easy to understand but in the case that you need it to be broken down I have given a breif breakdown below.

We declare our structure which has a bit of a different anatomy than a standard data type, instead this data type holds what seems to be a json value. This is known as a tagged data type which vasically defines metadata or instructions to the encoding/json package or other libraries that may use these special tags. Typically, you only see this in programs that may be using JSON to send or parse server responses, load configuration files, load settings files or is storing data in specific formats for the use of code translation. In our main function, we can see that we take our structure and specify data like normal and then finally convert it to json by calling `json.Marshal` which will convert the data as required. 

Our output may be something like the following 

```
{"name":"John Doe","age":30,"email":"johndoe@example.com"}
```

> `Struct` | Method Sets 

Method sets with structures is basically a way to define a function or method within a structure where that structure can only access that function. Below is an example of a program that creates a structure that utilizes method sets.

```go
package main

import (
	"fmt"
	"math"
)

type Circle struct {
	Radius float64
}

func (c Circle) Area() float64 {
	return math.Pi * c.Radius * c.Radius
}

func main() {
	c := Circle{Radius: 10.4}
	fmt.Println(c.Area())
}
```

As you can see, like any normal structure we declare the variables we need inside of the circle structure and then we create a method structure to calc the area of a circle. This function can not be called without properly initializing the `Circle` structure. When we declare a valid structure and use 10.4 as the radius we can then call the function to get the area of the circle.


## Sub Page -> Go Modules

When it comes to writing bigger projects in language's like Golang, you might find yourself needing to use multiple files, this module will help you understand the structure of modules in golang and how to properly use them. This module will also contain information over the rule sets.

> `Modules` | Rules

When it comes to importing specific files or rather modules since Go does not have a direct "concept of files", you need to follow rules. These rules help the compiler understand what you are trying to create and what you are trying to achomplish by importing what. Now, below I have named a chart of the primary rules for importing modules in Go.

| Rule | Compiler Error | Example Error |
| --- | --- | --- |
| Import path must be enclosed in double quotes | `import "mypackage"` | `import mypackage` |
| Imported package must be available in the Go module or standard library | `import "fmt"` | `import "nonexistent"` |
| Unused imported packages result in a compilation error | N/A | `import "unused"` |
| Importing a package but not using any of its exported symbols will cause a compilation error | N/A | `import _ "unused"` |
| Cyclic imports are not allowed | N/A | N/A |

These rules might be quite confusing so lets break it down a bit 

> Import path must be enclosed in double quotes 

This error means that the import path was not enclosed using `"` or `"`. Importing must be enclosed in either `""` or ` `` ` marks

> Importing package must be avalible in the go module or standard library 

This can mean that the module you tried to import does not exist within the standard library or does not exist within your .mod file configuration

> Unused import packages 

This means that you imported a package but did not use it 

```go
package main 

import "fmt"

func main() {
	println("hello")
}
```

this program called println not `fmt.Println()` so `fmt` is unused 

> Importing a package but not using any of its exported symbols 

same thing as unused import but instead importing as for example

```
package main 

import f "fmt"

func main() {
     println("hi")
}
```

>  Cyclic imports are not allowed

This basically means that a package that depends on another package can not be imported.

For example a cyclic import occurs when two or more packages depend on each other directly or indirectly this means that it creates a circular dependency where Package A imports Package B, and Package B also imports Package A, either directly or through a chain of dependencies.

Importing rules are pretty easy to understand but can become a pain if you do not exactly know what you are and arent using.


> `Modules` | Creating Packages

When it comes to creating modules in Golang, it can be quite confusing for people so lets walk through a small module that allows you to auto calculate specific numbers. 

We have a file tree that looks like this 

```
Project
├── go.mod
├── main.go
└── Modules
    ├── Add.go
    └── Sub.go

1 directory, 4 files
```

We first notice that there is a `go.mod` file within the directory tree, how did we get that file? In order to make project files or modules we must first create a go.mod file. The program we are going to be building is a simple calculator that can add and subtract two numbers `x` and `y`. With that information, we want our main module to be `Calc` thus the command `go mod init Calc` which will create a `go.mod` file that looks like the one below.

```go
module Calc

go 1.17
```

The module is the module name in this case Calc and the `go 1.17` is the version of the programming language. Simple file, now what does this mean? This means that anytime we import a filepath or module we need to use this filepath to import a module. So, within our go.mod file we need to import "Calc/Modules" as we can not directly import the "Modules" file path if it is not assigned the module within the `go.mod` file. Lets take a peek at our `main.go` file and see whats inside.


```go
package main

import (
	Caclulation_Module "Calc/Modules"
	"fmt"
)

func main() {
	r1 := Caclulation_Module.Add(20, 30)
	r2 := Caclulation_Module.Subtract(20, 30)
	fmt.Println("Added      | 20 + 30 = ", r1)
	fmt.Println("Subtracted | 20 / 30 = ", r2)
}
```

When we look at this file we see that we are importing the `Calc/Modules` package with the name `Calculation_Module` which is how we will call functions or variables from those packages.

We have two functions corresponding to our file names which are called `Add` and `Subtract` which will add and subtract two values. When we look in both files we see the following.

**Add.go**

```go
package Calculator

func Add(x, y int) int {
	return x + y
}
```

**Sub.go**

```go
package Calculator

func Subtract(x, y int) int {
	return x - y
}
```

Notice how each file has the same package name `Calculator`? This is because Go wants you to add the name of the package that is defined within that same exact directory, if we were to create a folder for each individual package or source code file then we could add individual names but then we would need to change our `main.go` file to import both of those individual sub paths.

Another note is that you see how each function starts with a capital letter? Golang will only allow you to use functions, variables, structures, imports etc ONLY if they start with a capital letter. This is because Golang only wants to export specific groups rather than everything. This allows the developer to have more control over what they want to be exported into the primary environment. You will also see this in every standard library that Golang has, every function or variable called will have a capital letter at the start of it.

> `Modules` | Using third party packages 

Something quite amazing about go is that it does not require a direct package installer like PyPi or Gem or even specific domain names or services to be used. Instead, golang will be able to download a specific package as long as it has a go.mod file within its root, this means that files can be downloaded from quite a large variety of hosting services. The program shown below uses the gopacket third party library to capture packets and print them out!

```go
package main

import (
	"fmt"
	"log"
	"os"

	"github.com/google/gopacket"
	"github.com/google/gopacket/pcap"
)

func main() {
	// Define the network interface to capture packets from
	device := "eth0"

	// Open the device for packet capture
	handle, err := pcap.OpenLive(device, 65536, true, pcap.BlockForever)
	if err != nil {
		log.Fatal(err)
	}
	defer handle.Close()

	// Set packet filter (optional)
	filter := "tcp and port 80"
	if err := handle.SetBPFFilter(filter); err != nil {
		log.Fatal(err)
	}

	// Start capturing packets
	packetSource := gopacket.NewPacketSource(handle, handle.LinkType())

	// Process captured packets
	for packet := range packetSource.Packets() {
		fmt.Println(packet)
	}
}
```

But how do we install this library? We can use a command known as `go get` to install this library!

`go get github.com/google/gopacket`

this command will install it and add it to your `go.sum` file which looks like the one shown below!

```go
github.com/google/gopacket v1.1.19 h1:ves8RnFZPGiFnTS0uPQStjwru6uO6h+nlr9j6fL7kF8=
github.com/google/gopacket v1.1.19/go.mod h1:iJ8V8n6KS+z2U1A8pUwu8bW5SyEMkXJB8Yo/Vo+TKTo=
golang.org/x/crypto v0.0.0-20190308221718-c2843e01d9a2/go.mod h1:djNgcEr1/C05ACkg1iLfiJU5Ep61QUkGW8qpdssI0+w=
golang.org/x/crypto v0.0.0-20191011191535-87dc89f01550/go.mod h1:yigFU9vqHzYiE8UmvKecakEJjdnWj3jj499lnFckfCI=
golang.org/x/lint v0.0.0-20200302205851-738671d3881b/go.mod h1:3xt1FjdF8hUf6vQPIChWIBhFzV8gjjsPE/fR3IyQdNY=
golang.org/x/mod v0.1.1-0.20191105210325-c90efee705ee/go.mod h1:QqPTAvyqsEbceGzBzNggFXnrqF1CaUcvgkdR5Ot7KZg=
golang.org/x/net v0.0.0-20190404232315-eb5bcb51f2a3/go.mod h1:t9HGtf8HONx5eT2rtn7q6eTqICYqUVnKs3thJo3Qplg=
golang.org/x/net v0.0.0-20190620200207-3b0461eec859/go.mod h1:z5CRVTTTmAJ677TzLLGU+0bjPO0LkuOLi4/5GtJWs/s=
golang.org/x/sync v0.0.0-20190423024810-112230192c58/go.mod h1:RxMgew5VJxzue5/jJTE5uejpjVlOe/izrB70Jof72aM=
golang.org/x/sys v0.0.0-20190215142949-d0b11bdaac8a/go.mod h1:STP8DvDyc/dI5b8T5hshtkjS+E42TnysNCUPdjciGhY=
golang.org/x/sys v0.0.0-20190412213103-97732733099d/go.mod h1:h1NjWce9XRLGQEsW7wpKNCjG9DtNlClVuFLEZdDNbEs=
golang.org/x/sys v0.8.0/go.mod h1:oPkhp1MJrh7nUepCBck5+mAzfO9JrbApNNgaTdGDITg=
golang.org/x/term v0.8.0/go.mod h1:xPskH00ivmX89bAKVGSKKtLOWNx2+17Eiy94tnKShWo=
golang.org/x/text v0.3.0/go.mod h1:NqM8EUOU14njkJ3fqMW+pc6Ldnwhi/IjpwHt7yyuwOQ=
golang.org/x/tools v0.0.0-20200130002326-2f3ba24bd6e7/go.mod h1:TB2adYChydJhpapKDTa4BR/hXlZSLoq2Wpct/0txZ28=
golang.org/x/xerrors v0.0.0-20191011141410-1b5146add898/go.mod h1:I/5z698sn9Ka8TeJc9MKroUUfqBBauWjQqLJ2OPfmY0=
```

what are all of these doing here? Well, third party packages rely on other third party packages which is why we 
see so many different packages here! But you may be confused why the go.sum file contains cryptographic hashes within each package. Well, golang does this to make sure that the original information has not been tampered with since it has been downloaded and added to the repo. These hashes can basically allow golang to verify that information. Go does this so it can provide stronger guarantees of package integrity and security in turn it helps prevent potential attacks where an adversary might try to inject malicious code into a package or intercept and modify the package during download.

Now we can easily use these third party packages! 

# Module (GoSecurity Related Development) 

This module will talk about specific use case's for the Go programming language and explain specific programs that will help you better analyze everything. For context, this will all be split into their own sub sections based on their type of usage or topic. For example, forensics will have its own section ( file forensics ) where the tree will look something like this.

```
GoSecurity
	|
	|- Forensics
		| File catching
		| File Parsing
		| File checking
	|- Cryptography / Encoding
		| Encodings
		| Ciphers
  		| Encryption algorithms
		| Encrypting files
```

As this structure works much better for organization than just shoving everything into one single file.

## Sub Page | Go File Forensics

File forensics is quite a large part of digital forensics, sometimes, you do not need to run the biggest tool to detect a file as you may just want something that can detect specific file headers or even specific signature. The list of programs in this module will allow you to inspect or categorize specific files much easily!

> File Forensics | Locating ZIP / Archives inside of images

Locating ZIP files is something that always confuses people, why is it required? why would a digital forensics expert need to know how to do it? In the case of malware or even general scenarios, we may need to check if ZIP's exist in images as images may be used to sneak past security measures. To do so, we can use the following code.

```go
package main


import (
   "bufio"
   "bytes"
   "fmt"
   "log"
   "os"
)

// Automate error checking
func CE(x error) {
   if x != nil {
       log.Fatal(x)
   }
}


func VerifyZipSig(k string) {
   sig := `\x4b\x03\x04` // ZIP / Archive signature (0x4b,0x03, 0x04)
   fmt.Printf("[%s]---[%s] Is being checked for a ZIP signature \n", "Debug", sig)
   f, x := os.Open(k) // Open file
   CE(x) // Check for error
   defer f.Close() // Close the file when the block of code is done executing
   buffer := bufio.NewReader(f) // create a new reader
   stat, _ := f.Stat() // stat the file to grab the files size
   for l := int64(0); l < stat.Size(); l++ { // itterate over the size
       b, x := buffer.ReadByte() // read the byte
       CE(x) // check for an error
       if b == '\x50' { // check if the byte is 0x50 ( if the first byte is '\x50' before performing the more expensive buffer.Peek(3) operation, the code can quickly identify that a potential ZIP signature might exist in the file. This check helps to reduce unnecessary calls to buffer.Peek(3) and improve the efficiency of the overall search process. )
           BS := make([]byte, 3) // Create the storage and buffer for the signature
           BS, x = buffer.Peek(3) 
           CE(x) // Check error
           if bytes.Equal(BS, []byte{'\x4b', '\x03', '\x04'}) {
               fmt.Println("File [ ", k, " ] Contains a ZIP file")
           } // Check and make sure that the ZIP signature accutally exists
       }
   }
}


// Main programatic entry point
func main() {
   if len(os.Args) == 0 { // os arguments
       fmt.Printf("Usage: %s image_file...", os.Args[0])
   } else {
       for _, f := range os.Args[1:] { // get all files from the argument list 'go run main.go file1.png file2.png file3.jpg ....'
           VerifyZipSig(f) // call function
       }
   }
}
```

This program works by scanning over each byte within the file or image and then compares it to the byte array for the signature of a ZIP file. If it is found it will say that the given file followed by its name does in fact contain a zip signature. If the file does contain a ZIP signature you can use 7z to extract the ZIP file.

> File Forensics | Cuting out sections of images 

When it comes to digital forensics specifically files, it may come in handy one day where you need to just slice an image in half or even cut out otherwise known as `carve` a part of a file out to make sure you are parsing a specific bit. This allows you to be much more percise when it comes to your investigations. The program below will do so but will allow you to cut from a starting point to an ending point.

```go
package main

import (
   "fmt"
   "io/ioutil"
   "log"
   "os"
)

// Stop cutting at...
var endB = []byte{0x00, 0x00}

var startb = []byte{
       0x5b, 0xce, 0xb7,
       0x14, 0x0c, 0x00,
       0x00, 0x00, 0x0c,
       0x00, 0x00, 0x00,
       0x0d, 0x00, 0x00,
       0x00,
} // Define the starting bytes to cut

// Automate errors
func CE(msg string, x error) {
   if x != nil {
       log.Fatal(msg + " -> " + fmt.Sprint(x))
   }
}

// Carving function
func Carve(file string) {
   in, x := ioutil.ReadFile(file) // Read the file into bytes
   CE("Could not read the input file  ", x) // Check error
   var start, end int // define start and end points
   for i := 0; i < len(in)-len(startb); i++ { // itterate over the length
       if string(in[i:i+len(startb)]) == string(startb) { // calculate the start
           start = i + len(startb)
           break
       }
   }
   for i := len(in) - len(endB); i > 0; i-- { // itterate over the length
       if string(in[i:i+len(endB)]) == string(endB) { // calculate the end
           end = i
           break
       }
   } // check if the start and end are within bounds
   if start >= end {
       fmt.Println("File signature not found")
       os.Exit(0)
   }
   outputFile, x := os.Create("output.jpg") // create output file
   CE("Could not CREATE the output file ", x) // check for error
   defer outputFile.Close() // close file at the end of the brick
   _, x = outputFile.Write(in[start:end]) // write the cut start to the cutting end point
   CE("Could not WRITE output file ", x) // check for the error
   fmt.Println("File carved successfully") // output the write message OK
}


func main() {
   if len(os.Args) == 0 {
       fmt.Println("Usage: " + os.Args[0] + " input_file.jpg")
   } else {
       Carve(os.Args[1])
   }
}
```

This program you will need to tweak a bit, but here is how we might use this tool. Say we have a picture that has a ZIP file inside of it. We can demo this with an image dump shown below.

```
00000000  50 4b 03 04 14 03 00 00  00 00 85 91 bc 56 00 00  |PK...........V..|
00000010  00 00 00 00 00 00 00 00  00 00 0c 00 00 00 43 6f  |..............Co|
00000020  6d 70 72 65 73 73 44 69  72 2f 50 4b 03 04 14 03  |mpressDir/PK....|
00000030  00 00 08 00 1a 93 b8 56  01 a1 cd f1 3f 00 00 00  |.......V....?...|
00000040  7e 00 00 00 16 00 00 00  43 6f 6d 70 72 65 73 73  |~.......Compress|
00000050  44 69 72 2f 62 61 6e 6e  65 72 2e 74 78 74 e3 04  |Dir/banner.txt..|
00000060  02 85 47 53 fa 1f 4d 69  7c 34 65 32 17 88 fb 68  |..GS..Mi|4e2...h|
00000070  4a 33 10 29 00 31 88 ab  00 04 20 49 04 9a 0d 12  |J3.).1.... I....|
00000080  d6 02 0a 03 31 88 04 72  21 7c b0 38 50 03 10 83  |....1..r!|.8P...|
00000090  09 88 04 5c 09 94 d6 82  99 0a 64 01 00 50 4b 03  |...\......d..PK.|
000000a0  04 14 03 00 00 08 00 87  7a bc 56 50 9b 38 0b 30  |........z.VP.8.0|
000000b0  00 00 00 89 00 00 00 14  00 00 00 43 6f 6d 70 72  |...........Compr|
000000c0  65 73 73 44 69 72 2f 6d  61 69 6e 2e 74 78 74 e3  |essDir/main.txt.|
000000d0  e2 04 02 05 05 85 e0 ec  4a 05 9f cc bc 54 05 cf  |........J....T..|
000000e0  bc 92 d4 a2 82 a2 54 20  59 a3 10 a6 60 a0 67 a0  |......T Y...`.g.|
000000f0  67 0a 53 84 4a 53 09 14  a7 26 03 6d e3 02 00 50  |g.S.JS...&.m...P|
00000100  4b 01 02 3f 03 14 03 00  00 00 00 85 91 bc 56 00  |K..?..........V.|
00000110  00 00 00 00 00 00 00 00  00 00 00 0c 00 24 00 00  |.............$..|
00000120  00 00 00 00 00 10 80 ed  41 00 00 00 00 43 6f 6d  |........A....Com|
00000130  70 72 65 73 73 44 69 72  2f 0a 00 20 00 00 00 00  |pressDir/.. ....|
00000140  00 01 00 18 00 80 c2 e1  71 b1 91 d9 01 80 b4 ba  |........q.......|
00000150  6a b1 91 d9 01 80 c2 e1  71 b1 91 d9 01 50 4b 01  |j.......q....PK.|
00000160  02 3f 03 14 03 00 00 08  00 1a 93 b8 56 01 a1 cd  |.?..........V...|
00000170  f1 3f 00 00 00 7e 00 00  00 16 00 24 00 00 00 00  |.?...~.....$....|
00000180  00 00 00 20 80 a4 81 2a  00 00 00 43 6f 6d 70 72  |... ...*...Compr|
00000190  65 73 73 44 69 72 2f 62  61 6e 6e 65 72 2e 74 78  |essDir/banner.tx|
000001a0  74 0a 00 20 00 00 00 00  00 01 00 18 00 80 bb 6a  |t.. ...........j|
000001b0  8e 8e 8e d9 01 80 b3 bb  5e 8e 8e d9 01 00 ff 17  |........^.......|
000001c0  70 b1 91 d9 01 50 4b 01  02 3f 03 14 03 00 00 08  |p....PK..?......|
000001d0  00 87 7a bc 56 50 9b 38  0b 30 00 00 00 89 00 00  |..z.VP.8.0......|
000001e0  00 14 00 24 00 00 00 00  00 00 00 20 80 a4 81 9d  |...$....... ....|
000001f0  00 00 00 43 6f 6d 70 72  65 73 73 44 69 72 2f 6d  |...CompressDir/m|
00000200  61 69 6e 2e 74 78 74 0a  00 20 00 00 00 00 00 01  |ain.txt.. ......|
00000210  00 18 00 80 14 11 6d 99  91 d9 01 80 14 11 6d 99  |......m.......m.|
00000220  91 d9 01 80 c2 e1 71 b1  91 d9 01 50 4b 05 06 00  |......q....PK...|
00000230  00 00 00 03 00 03 00 2c  01 00 00 ff 00 00 00 00  |.......,........|
00000240  00                                                |.|
00000241
```

we can take specific bytes we want to carve out and run this program. Say we want to carve anything from `f1 3f 00 00 00 7e 00 00  00 16 00 24 00 00 00 00` to `0x00` which is the end of the file in this case. We can replace our current hex with the following

```go
var endB = []byte{0x00}

var startb = []byte{
	0xf1, 0x3f, 0x00, 
	0x00, 0x00, 0x7e, 
	0x00, 0x00, 0x00, 
	0x16, 0x00, 0x24, 
	0x00, 0x00, 0x00, 
	0x00} // Define the starting bytes to cut
```

When we run the program and get our output we should get something like

```
 f1 3f 00 00 00 7e 00 00  00 16 00 24 00 00 00 00  |.?...~.....$....|
00000180  00 00 00 20 80 a4 81 2a  00 00 00 43 6f 6d 70 72  |... ...*...Compr|
00000190  65 73 73 44 69 72 2f 62  61 6e 6e 65 72 2e 74 78  |essDir/banner.tx|
000001a0  74 0a 00 20 00 00 00 00  00 01 00 18 00 80 bb 6a  |t.. ...........j|
000001b0  8e 8e 8e d9 01 80 b3 bb  5e 8e 8e d9 01 00 ff 17  |........^.......|
000001c0  70 b1 91 d9 01 50 4b 01  02 3f 03 14 03 00 00 08  |p....PK..?......|
000001d0  00 87 7a bc 56 50 9b 38  0b 30 00 00 00 89 00 00  |..z.VP.8.0......|
000001e0  00 14 00 24 00 00 00 00  00 00 00 20 80 a4 81 9d  |...$....... ....|
000001f0  00 00 00 43 6f 6d 70 72  65 73 73 44 69 72 2f 6d  |...CompressDir/m|
00000200  61 69 6e 2e 74 78 74 0a  00 20 00 00 00 00 00 01  |ain.txt.. ......|
00000210  00 18 00 80 14 11 6d 99  91 d9 01 80 14 11 6d 99  |......m.......m.|
00000220  91 d9 01 80 c2 e1 71 b1  91 d9 01 50 4b 05 06 00  |......q....PK...|
00000230  00 00 00 03 00 03 00 2c  01 00 00 ff 00 00 00 00  |.......,........|
00000240  00                                                |.|
00000241
```
cut out in the resulting file.


> File Forensics | Hex Conversion

This is not really a file forensics thing but may become helpful to you. Sometimes, manually converting thousands of hex points for forensics, shellcode etc can be quite boring. The following utility will allow you to convert these bytes into actual hex.

```go
package main

import (
	"fmt"
	"os"
	"strings"
)

func main() {
	// Input code
	input := os.Args[1]
	// Split the input by space to get individual codes
	codes := strings.Split(input, " ")
	// Convert each code to its hex representation
	var hexCodes []string
	for _, code := range codes {
		hexCode := fmt.Sprintf("0x%s", code)
		hexCodes = append(hexCodes, hexCode)
	}
	// Print the hex representation
	fmt.Println(strings.Join(hexCodes, ", "))
}
```

**Testing**

When we test the program with `go run hexutil.go "f1 3f 00 00 00 7e 00 00 00 16 00 24 00 00 00 00"` we get `0xf1, 0x3f, 0x00, 0x00, 0x00, 0x7e, 0x00, 0x00, 0x00, 0x16, 0x00, 0x24, 0x00, 0x00, 0x00, 0x00`

> File Forensics | Getting mime type

Sometimes, the OS can not detect a specific file type, this is where file checking tools come in handy. Of course, tools like `file` exist on linux to get the file type, but this tool may work in any other environment where you may not be on linux or in some wild instance where `file` is not directly implemented. The program below will catch a file's mime type based on structured data.

```go
package main


import (
   "bytes"
   "fmt"
   "io/ioutil"
   "os"
   "strings"
)


type Signatures struct {
   Sign   string
   Sufix  string
   Format string
}

var Sig = []Signatures{
	{`62706C69`, `*.bplist`, `Binary Property List`},
	{`006E1EF0`, `*.ppt`, `PPT`},
	{`A0461DF0`, `*.ppt`, `PPT`},
	{`ECA5C100`, `*.doc`, `Doc file`},
	{`474946`, `*.gif`, `GIF files`},
	{`GIF89a`, `*.gif`, `GIF files`},
	{`FFD8FF`, `*.jpg`, `JPEG files`},
	{`JFIF`, `*.jpg`, `JPEG files`},
	{`504B03`, `*.zip`, `ZIP files`},
	{`LfLe`, `*.evt`, `Event file`},
	{`38425053`, `*.psd`, `Photoshop file`},
	{`8BPS`, `*.psd`, `Photoshop file`},
	{`4D5A`, `*.ocx`, `Active X`},
	{`415649204C495354`, `*.avi`, `AVI file`},
	{`AVI LIST`, `*.avi`, `AVI file`},
	{`57415645666D7420`, `*.wav`, `WAV file`},
	{`WAVEfmt`, `*.wav`, `WAV file`},
	{`25504446`, `*.pdf`, `PDF files`},
	{`%PDF`, `*.pdf`, `PDF files`},
	{`000100005374616E64617264204A6574204442`, `*.mdb`, `Microsoft database`},
	{`Standard Jet DB`, `*.mdb`, `Microsoft database`},
	{`2142444E`, `*.pst`, `PST file`},
	{`!BDN`, `*.pst`, `PST file`},
	{`4D6963726F736F66742056697375616C2053747564696F20536F6C7574696F6E2046696C65`, `*.sln`, `Microsft SLN file`},
	{`Microsoft Visual Studio Solution File`, `*.sln`, `Microsft SLN file`},
	{`504B030414000600`, `*.docx`, `Microsoft DOCX file`},
	{`504B030414000600`, `*.pptx`, `Microsoft PPTX file`},
	{`504B030414000600`, `*.xlsx`, `Microsoft XLSX file`},
	{`504B0304140008000800`, `*.xlsx`, `Java JAR file`},
	{`0908100000060500`, `*.xls`, `XLS file`},
	{`D0CF11E0A1B11AE1`, `*.msi`, `MSI file`},
	{`D0CF11E0A1B11AE1`, `*.doc`, `DOC`},
	{`D0CF11E0A1B11AE1`, `*.xls`, `Excel`},
	{`D0CF11E0A1B11AE1`, `*.vsd`, `Visio`},
	{`D0CF11E0A1B11AE1`, `*.ppt`, `PPT`},
	{`0A2525454F460A`, `*.pdf`, `PDF file`},
	{`.%%EOF.`, `*.pdf`, `PDF file`},
	{`4040402000004040`, `*.hlp`, `HLP file`},
	{`465753`, `*.swf`, `SWF file`},
	{`FWS`, `*.swf`, `SWF file`},
	{`CWS`, `*.swf`, `SWF file`},
	{`494433`, `*.mp3`, `MP3 file`},
	{`ID3`, `*.mp3`, `MP3 file`},
	{`MSCF`, `*.cab`, `Cab file`},
	{`0x4D534346`, `*.cab`, `Cab file`},
	{`ITSF`, `*.chm`, `Compressed Help`},
	{`49545346`, `*.chm`, `Compressed Help`},
	{`4C00000001140200`, `*.lnk`, `Link file`},
	{`4C01`, `*.obj`, `OBJ file`},
	{`4D4D002A`, `*.tif`, `TIF graphics`},
	{`MM`, `*.tif`, `TIF graphics`},
	{`000000186674797033677035`, `*.mp4`, `MP4 Video`},
	{`ftyp3gp5`, `*.mp4`, `MP4 Video`},
	{`0x00000100`, `*.ico`, `Icon file`},
	{`300000004C664C65`, `*.evt`, `Event file`},
	{`Rar!`, `*.rar`, `RAR file`},
	{`526172211A0700`, `*.rar`, `RAR file`},
	{`52657475726E2D506174683A20`, `*.eml`, `EML file`},
	{`Return-Path:`, `*.eml`, `EML file`},
	{`6D6F6F76`, `*.mov`, `MOV file`},
	{`moov`, `*.mov`, `MOV file`},
	{`7B5C72746631`, `*.rtf`, `RTF file`},
	{`{\rtf1`, `*.rtf`, `RTF file`},
	{`89504E470D0A1A0A`, `*.png`, `PNG file`},
	{`PNG`, `*.png`, `PNG file`},
	{`C5D0D3C6`, `*.eps`, `EPS file`},
	{`CAFEBABE`, `*.class`, `Java class file`},
	{`D7CDC69A`, `*.WMF`, `WMF file`},
}

func main() {
   if len(os.Args) == 0 {
       fmt.Printf("Usage: %s unknownfile... ", os.Args[0])
   } else {
       for _, file := range os.Args[1:] {
           f, _ := ioutil.ReadFile(file) // skip bad files
           for _, v := range Sig {
               if strings.HasSuffix(file, v.Sufix) || bytes.Contains(f, []byte(v.Sign)) {
                   fmt.Println("File [ " + file + " ] was picked up as a [ " + v.Format + " ] using symbol < " + fmt.Sprint([]byte(v.Sign)) + " > ")
                   continue
               }
           }
       }
   }
}
```

This list can be improved but this is a good example of how you might do this.

> File Forensics | PE File forensics 

File forensics may not just be for specific file groups but rather file types. Take this program that parsers and grabs values for PE files

```go
package main

import (
	"debug/pe"
	"encoding/binary"
	"fmt"
	"io"
	"log"
	"os"
)

var (
	SizeofOptionalHeader32 = uint16(binary.Size(pe.OptionalHeader32{}))
	SizeofOptionalHeader64 = uint16(binary.Size(pe.OptionalHeader64{}))
	X32                    pe.OptionalHeader32
	X64                    pe.OptionalHeader64
)

func CE(x error) {
	if x != nil {
		log.Fatal(x)
	}
}

func main() {
	f, x := os.Open(os.Args[0])
	CE(x)
	PEFILE, x := pe.NewFile(f)
	CE(x)
	defer f.Close()
	defer PEFILE.Close()
	HEAD := make([]byte, 96)
	so := make([]byte, 4)
	_, x = f.Read(HEAD)
	CE(x)
	peoffset := int64(binary.LittleEndian.Uint32(HEAD[0x3c:]))
	f.ReadAt(so[:], peoffset)
	sr := io.NewSectionReader(f, 0, 1<<63-1)
	_, x = sr.Seek(peoffset+4, io.SeekStart)
	CE(x)
	binary.Read(sr, binary.LittleEndian, &PEFILE.FileHeader)
	switch PEFILE.FileHeader.SizeOfOptionalHeader {
	case SizeofOptionalHeader32:
		binary.Read(sr, binary.LittleEndian, &X32)
	case SizeofOptionalHeader64:
		binary.Read(sr, binary.LittleEndian, &X64)
	}
	fmt.Printf("Magic byte                      : %s%s\n", string(HEAD[0]), string(HEAD[1]))
	fmt.Printf("LFA_NEW Value                   : %s\n", string(so))
	fmt.Printf("Architecture                    : %#x\n", PEFILE.FileHeader.Machine)
	fmt.Printf("Section Count                   : %#x\n", PEFILE.FileHeader.NumberOfSections)
	fmt.Printf("Sizeof Op Header                : %#x\n", PEFILE.FileHeader.SizeOfOptionalHeader)
	fmt.Printf("Num of section field offsets    : %#x\n", peoffset+6)
	fmt.Printf("Section Table offset            : %#x\n", peoffset+0xF8)
	for _, sn := range PEFILE.Sections {
		fmt.Printf("|>>> Discovered Section %s\n", sn.Name)
		fmt.Printf("\tSection Characteristics              | %#x\n", sn.Characteristics)
		fmt.Printf("\tSection Virtual Size                 | %#x\n", sn.VirtualSize)
		fmt.Printf("\tSection Virtual Offset               | %#x\n", sn.VirtualAddress)
		fmt.Printf("\tSection Raw Size                     | %#x\n", sn.Size)
		fmt.Printf("\tSection Raw Offset to Data           |%#x\n", sn.Offset)
		fmt.Printf("\tSection Append Offset (Next Section) | %#x\n", sn.Offset+sn.Size)
	}
	fmt.Printf("Entry Point                | %#x\n", X32.AddressOfEntryPoint)
	fmt.Printf("Image Base                 | %#x\n", X32.ImageBase)
	fmt.Printf("Size of image              | %#x\n", X32.SizeOfImage)
	fmt.Printf("Section alignment          | %#x\n", X32.SectionAlignment)
	fmt.Printf("File attachment            | %#x\n", X32.FileAlignment)
	fmt.Printf("File Characteristics       | %#x\n", PEFILE.FileHeader.Characteristics)
	fmt.Printf("Size of headers            | %#x\n", X32.SizeOfHeaders)
	fmt.Printf("Checksum                   | %#x\n", X32.CheckSum)
	fmt.Printf("Machine                    | %#x\n", PEFILE.FileHeader.Machine)
	fmt.Printf("Subsystem                  | %#x\n", X32.Subsystem)
	fmt.Printf("DLL Characteristics        | %#x\n", X32.DllCharacteristics)
}
```

There are many more advanced ways we can parse this information but this is another good example of how go allows you to quickly execute operations like this.

## Sub Page | Go Cryptography / Encoding

Encoding is a major part of cyber security related operations. Sometimes you may need to actually encode payloads or decode data using base64 or in more extreme cases ROT13. Below I have a few frameworks and programs that can actually help you understand encryption, ciphers and encodings.

> Cryptography / Encoding | Encoding's ( base64/base32 )

There are many encodings go has built directly into its standard library and one of the more used encodings is the base set of encodings! The program below takes input text, detects if its a specific base encoding and decodes the text.

For context, bases in this means that it detected, encodes and decodes base64 and base32 strings.

```go
package main

import (
	"encoding/base32"
	"encoding/base64"
	"fmt"
)

type BaseDecoder struct {
	Base64decoded []byte
	Base32decoded []byte
}

var (
	X  error
	BD BaseDecoder
)

func DetectBase32(input string) bool {
	BD.Base32decoded, X = base32.StdEncoding.DecodeString(input)
	return X == nil
}

func DetectBase64(input string) bool {
	BD.Base64decoded, X = base64.StdEncoding.DecodeString(input)
	return X == nil
}

func EncodeB64(input string) string {
	return base64.RawStdEncoding.EncodeToString([]byte(input))
}

func EncodeB32(input string) string {
	return base32.StdEncoding.EncodeToString([]byte(input))
}

func main() {
	base32String := EncodeB32("foobar")
	base64String := EncodeB64("Hello World!")
	isBase32 := DetectBase32(base32String)
	isBase64 := DetectBase64(base64String)
	if isBase32 {
		fmt.Println("[+] Found encoding! (BASE32)[" + base32String + "]")
		fmt.Println(string(BD.Base32decoded))
	}
	if isBase64 {
		fmt.Println("[+] Found encoding! (BASE32)[" + base64String + "]")
		fmt.Println(string(BD.Base64decoded))
	}
}
```

This program is very easy to understand as we can see we just call base32 an base64 libraries. 

Cryptography / Encoding | Ciphers (Rot13, Beacon Cipher, Vig


