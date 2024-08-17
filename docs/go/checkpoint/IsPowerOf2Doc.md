# Is Power Of 2

IsPowerOf2 is a function that will take an argument and return true if the number given is a power of 2, otherwise it returns false.  

```txt
2² = 2 * 2 = 4  
2³ = 2 * 2 * 2 = 8
ect
```

## Functions

This exercice allow the use of the strconv package, that will allow us to convert our argument into an int.

We will use a function called PrintStr that will allow us to print strings (true and false here).  
```go
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}
```

## IsPowerOf2 step by step

### First step

We first need to check if we have only one argument:
```go
if len(os.Args) != 2 {
		return
	}
```
If not then we just end the program.  

### Second step

We convert the first argument into an int, to be able to compare it after.
```go
  number, err := strconv.Atoi(os.Args[1])
	if err != nil {
		return
	}
```
If the error isn't equal to nil, that means that our argument isn't an int, we then end the program.  

### Third and final step

We loop over the values of powers of 2.  
We do that by multiplying i by 2 as incrementation.  
```go
// The i inferior or equal to number is very important here
for i := 2; i <= number; i = i * 2 {
    // compare is at any time i is equal to our number
		if i == number {
			PrintStr("true")
			return
		}
	}
  // if we manage to get out of the loop without ending the program, that means our number isn't a power of 2
	PrintStr("false")
```
If i is equal to our number, then we Print "true" and end the program, otherwise we Print "false".

## Full code

```go
package main

import (
	"os"
	"strconv"
)

func IsPowerof2() {
  // first step
	if len(os.Args) != 2 {
		return
	}
  // second step
	number, err := strconv.Atoi(os.Args[1])
	if err != nil {
		return
	}
  // final step
	for i := 2; i <= number; i = i * 2 {
		if i == number {
			PrintStr("true")
			return
		}
	}
	PrintStr("false")
}
```