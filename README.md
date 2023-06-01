<p align="center">
  <img src="https://github.com/TotallyNotAHaxxer/MartianDefense-Golang-MDFiles/blob/main/Screenshot%20from%202023-05-30%2015-18-09.png">
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


