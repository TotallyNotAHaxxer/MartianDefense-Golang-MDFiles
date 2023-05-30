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


