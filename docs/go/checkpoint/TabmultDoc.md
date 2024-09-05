# Tabmult

## What's Tabmult

Tabmult is a function that displays a number's multiplication table.

The parameter will always be a **strictly positive number** that fits in an int. **Said number multiplied by 9 will also fit in an int.**  

## PrintStr function

We define a function called PrintStr that will allow us to print a string we will give to it.  
```go
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}
```

## Tabmult step by step

### First step

If the number of arguments is different from 2 (number + name of the file), then we end the programm.  

```go
if len(os.Args) != 2 {
	return
}
``` 

### Second step

We then store into a new variable the **convertion of our argument to an int** to be able to apply multiplications to it.  
```go
number, err := strconv.Atoi(os.Args[1])
	if err != nil {
		return
	}
```  
**Also we check for error, if for example the argument given isn't an int.**  

### Third step

We make a loop that will start at 1 and end at 9. That index will be the number that will multiply our converted os.Args[1].  
```go
for i := 1; i < 10; i++ {
}  
```

### Fourth and final step

We only need now to print our lines using our **PrintStr function.**  
We have to keep in mind that our function **only print strings, so we will have to convert the ints** into strings inside the function.  
```go
PrintStr(strconv.Itoa(i) + " x " + os.Args[1] + " = " + strconv.Itoa(i * number))
z01.PrintRune('\n')
```
**Note that we can add strings to eachothers and it will work like the append function works on arrays.**  

## Full code

```go
package main

import (
	"os"
	"strconv"

	"github.com/01-edu/z01"
)

func PrintStr(s string) {
	for i := 0; i < len(s); i++ {
		z01.PrintRune(rune(s[i]))
	}
}

func TabMult() {
	if len(os.Args) != 2 {
		return
	}
	number, err := strconv.Atoi(os.Args[1])
	if err != nil {
		return
	}
	for i := 1; i < 10; i++ {
		PrintStr(strconv.Itoa(i) + " x " + os.Args[1] + " = ")
		PrintStr(strconv.Itoa(i * number))
		z01.PrintRune('\n')
	}
}
```

