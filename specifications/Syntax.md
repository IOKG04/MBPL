# Syntax

The syntax of MBPL is based in mathematics, set theory in particular, with some common c like elements mixed in.

```
func Main(args ∈ [Strings]) ∈ ℕ -> {
    age ∈ ℕ <- ℕ(args[0]) ;
    if(¬if(age ≥ 18 ; print("You may pass")) ; print("You may not pass")) ;
    self <- 0
}
```

Functions cannot have any side effects (except IO) and always have to result in the same output given the same input.

---
## Functions

Functions are the foundation of MBPL and can be defined using `func [name]([arguments]) ∈ [output value type] -> { [...] }` for named functions and using `([arguments]) ∈ [output value type] -> { [...] }` for anonymous functions

[name] is replaced with the name of the function  
[arguments] is replaced with the arguments  
[output value type] is replaces with the output value type  
[...] is replaced with the statements to be executed  

```
func ExampleFunction(input ∈ ℤ) ∈ ℤ -> {
    self <- input + 1
}

(input ∈ ℤ) ∈ ℤ -> { self <- input + 1 }
```

Every function returns a value which can be specified using `self <- [value]` where [value] is the return value  
The value is returned after every statement is executed

Named functions can be called using `[name]([arguments])` where [name] is the name of the function and [arguments] is the arguments given to the function  
Anonymous functions can be called using `[definition]([arguments])` where [definition] is the definition of the function and [arguments] is the arguments given to the function  

Named function can only be defined globally and anonymous functions cannot be defined globally

---
## Variables

Variable are important to reuse data multiple times without recomputing every time and can be initialized using `[name] ∈ [value type]`, set using `[name] <- [value]` and initialized and set using `[name] ∈ [value type] <- [value]`

[name] is replaced with the name of the variable  
[value type] is replaced with the value type of the variable  
[value] is replaced with the new value of the variable  

```
foo ∈ ℤ ;
foo <- 10 ;

bar ∈ ℝ <- π
```

Variables cannot be global  

---
## Sets

Sets are value types functions can return, functions can take as arguments and variables can be and can be defined using `[name] -> [...]`

[name] is replaced with the name of the set  
[...] is replaced with the specification of the set  

```
Radian -> {
    value ∈ ℝ ;
    greaterequal(value ; 0) ;
    lessequal(value ; π)
}

StringIntegerPair -> {
    string ∈ Strings ;
    integer ∈ ℤ
}
```

If a set has multiple fields (like `StringIntegerPair` in the example) the separate fields can be accessed using `[name].[field name]` where [name] is the name of the variable or function and [field name] is the name of the field in the set  
Sets can have functions returning a Boolean as a limitation (like `Radian` in the example)

Sets can only be global

---
## General syntax

Statements and arguments are divided using ` ; `

Statements can be grouped into a larger statements using `{ [...] }` where [...] are the separate statements

Single line comments are indicated using `//` and multi line comments are started with `/*` and ended with `*/`

---
## Given

A few functions and sets are given by the programming language

### Given functions

`print(s ∈ Strings) ∈ ℕ` appends s to the standard output and returns 0 if successful  
`print(n ∈ ℤ) ∈ ℕ` appends the string representation of n to the standard output and returns 0 if successful (The same function exists for every other kind of number too)

`if(condition ∈ Boolean ; s ∈ Statements) ∈ Boolean` executes s if condition is true and returns condition  
`while(condition ∈ Boolean ; s ∈ Statements) ∈ ℕ` executes s while condition is true and returns the number of times s was executed  

`add(a ∈ ℤ ; b ∈ ℤ) ∈ ℤ` returns the sum of a and b (The same function exists for every other kind of number too)  
`subtract(a ∈ ℤ ; b ∈ ℤ) ∈ ℤ` returns the difference between a and b (The same function exists for every other kind of number too)  
`multiply(a ∈ ℤ ; b ∈ ℤ) ∈ ℤ` returns the product of a and b (The same function exists for every other kind of number too)  
`divide(a ∈ ℤ ; b ∈ ℤ) ∈ ℚ` returns the quotient of a and b (The same function exists for every other kind of number too)

`equal(a ∈ ℤ ; b ∈ ℤ) ∈ Boolean` returns true if a is equal to b (The same function exists for every other kind of given set too)  
`notequal(a ∈ ℤ ; b ∈ ℤ) ∈ Boolean` returns true if a is not equal to b (The same function exists for every other kind of given set too)  
`greater(a ∈ ℤ ; b ∈ ℤ) ∈ Boolean` returns true if a is greater than b (The same function exists for every other kind of number too)  
`greaterequal(a ∈ ℤ ; b ∈ ℤ) ∈ Boolean` returns true if a is greater than or equal to b (The same function exists for every other kind of number too)  
`less(a ∈ ℤ ; b ∈ ℤ) ∈ Boolean` returns true if a is less than b (The same function exists for every other kind of number too)  
`lessequal(a ∈ ℤ ; b ∈ ℤ) ∈ Boolean` returns true if a is less than or equal to b (The same function exists for every other kind of number too)

`not(b ∈ Boolean) ∈ Boolean` returns true if b is false and false if b is true  
`and(a ∈ Boolean ; b ∈ Boolean) ∈ Boolean` returns true if a and b are true and false otherwise  
`or(a ∈ Boolean ; b ∈ Boolean) ∈ Boolean` returns true if either a or b are true and false otherwise 

`ℤ(s ∈ Strings) ∈ ℤ` returns the integer of s (The same function exists for every other kind of number too)  
`ℤ(n ∈ ℝ) ∈ ℤ` returns the integer of n (The same function exists for every other kind of number too)  
`Strings(n ∈ ℤ) ∈ Strings` returns the string representation of n (The same function exists for every other kind of number too)

### Given sets

`ℕ` is the set of all natural numbers (0, 1, 2, 1024, etc)  
`ℤ` is the set of all integers (-3, 0, etc)  
`ℚ` is the set of all rational numbers (1/2, -7/15, 0, etc)  
`ℝ` is the set of all real numbers (sqrt(2), -π, 0, etc)

`Strings` is the set of all strings ("Meow", "", "Hello world!", etc)  
`Boolean` is the set of true and false  
`Functions` is the set of all functions  
`Statements` is the set of all executeable code snippets  
`[[t]]` where [t] is a set is the set of all lists with [t] as it's basis (normally known as an array of [t])

---
## Special

### Shortened functions

Some functions can be shortened to a character:

`add(a ∈ [t] ; b ∈ [t]) ∈ [t]` where [t] is a set can be shortened to `a + b`  
`subtract(a ∈ [t] ; b ∈ [t]) ∈ [t]` where [t] is a set can be shortened to `a - b`  
`multiply(a ∈ [t] ; b ∈ [t]) ∈ [t]` where [t] is a set can be shortened to `a * b`  
`divide(a ∈ [t] ; b ∈ [t]) ∈ [t]` where [t] is a set can be shortened to `a / b`

`equal(a ∈ [t] ; b ∈ [t]) ∈ Boolean` where [t] is a set can be shortened to `a = b`  
`notequal(a ∈ [t] ; b ∈ [t]) ∈ Boolean` where [t] is a set can be shortened to `a ≠ b`  
`greater(a ∈ [t] ; b ∈ [t]) ∈ Boolean` where [t] is a set can be shortened to `a > b`  
`greaterequal(a ∈ [t] ; b ∈ [t]) ∈ Boolean` where [t] is a set can be shortened to `a ≥ b`  
`less(a ∈ [t] ; b ∈ [t]) ∈ Boolean` where [t] is a set can be shortened to `a < b`  
`lessequal(a ∈ [t] ; b ∈ [t]) ∈ Boolean` where [t] is a set can be shortened to `a ≤ b`

`not(b ∈ [t]) ∈ [t]` where [t] is a set can be shortened to `¬b`  
`and(a ∈ [t] ; b ∈ [t]) ∈ [t]` where [t] is a set can be shortened to `a & b`  
`or(a ∈ [t] ; b ∈ [t]) ∈ [t]` where [t] is a set can be shortened to `a | b`
