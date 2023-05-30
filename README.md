<p align="center">
  <img src="https://github.com/TotallyNotAHaxxer/MartianDefense-Golang-MDFiles/blob/main/Screenshot%20from%202023-05-30%2015-18-09.png">
</p>

# Module introduction

This module within the Martian Defense gitbook goes over the Go programming language. The Go programming language is used quite often in the cyber security world and is much more worth it to learn than you might think. For context, Go is a statically typed, machine code compiled and versatile programming language that can be used for many security specific tasks such as reverse shells, cryptography, networking, server side and client side development and even malware development.

# Go | For Security 

Golang is a programming language that has many amazing features to it, so what exactly makes go suited for security specifically? In order to solve this, a table has been provided below.

| Feature | Reason for use in cyber security |
| ------- | -------------------------------- |
| Standard Library | Most language's currently used in cyber security realms that are interpreted such as python have a major issue with not providing the correct standard library to do exactly what you need. this leaves it completely up to the user to download and install third party libraries to complete the task they need to. Golang has an amazing standard library that makes it easy to setup requests, parse files, load specific information while also allowing for a much more versatile impact | 
| Type System | Unlike most programming language's, go has an amazing type system which holds data types such as rune, string, interface, byte, unsigned integers, big integers, integers, floats, complex numbers and even more mathematically detailed data types. This allows users to easily work with files, systems and type specific operations |
| Speed and performance | Golang is one of the faster more used programming language's because of the way it's compiler optimizes and generates code while also working with virtual tables! |
| Concurrency | Another amazing feature of the Go programming language is that it is a very very thread heavy language and has support for atomic, async, mutex and other various threading factors |

# Go | Introduction

Golang is a interesting programming language and has a weird syntax, so lets explain the rules of the compiler before we jump into everything.

> Golang | Files

Every programming language has some form of file system, it has some form of extension that is also run through the compiler or interpreter. Golang has multiple files which are placed in the table below.

| File type / Extension | Purpose or reason for use |
| --------------------- | ------------------------- |
| .go                   | Golang source code file. These types of files are where source code will come into handy |
| .mod                  | Golang Module file. These files are used for directories and module development which will be talked about later |
| .sum                  | Golang Module file which holds all the cryptographic signatures for third party libraries in use within the project |

> Golang | Entry Points

Like most compiled and statically typed lamguages such as C, C++, Assembler, Fortran etc Golang has a main entry point and a sub entry point that is optional. What do I mean when I say sub entry point and main entry point. The main entry point of a golang program is defined as `main` while a sub entry point is called `init`. These are both possible entry points that can be placed wherever in the file.

** the `init` sub entry point **

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

** The `main` entry point **

This is the actual program entry point within the program, this MUST be declared for a go program to run. To declare a main function we can do it as shown below.

```go
func main() {
    // main code and calls here
}
```

and when we run our program it will execute. 

** Clashing with init and main | Rules **

INIT functions CAN NOT BE CALLED. This is because the go compiler will prioritize these calls on the backend already and double calling an initation function is not directly supported or should be done anyway. 

Below is a list of rules for init and main functions 

> `init` or `main` functions can NOT be called by the user 
> In order to use a `init` function `main` must be declared
> `init` functions can be declared in any source code file 
> `main` functions have to be placed in a .go source code file with the package of `main`
