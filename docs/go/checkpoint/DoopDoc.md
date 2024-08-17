# Doop
Doop is a function that takes **3 command-line arguments: two numbers and an operator**, and performs the corresponding arithmetic operation.

## Functions

In this exercice you don't have access to strconv package, which contains the tools to transform int and strings.  
We will need to perform arithmetic operations on our arguments, that are strings, so we will have to convert them to int.  
To show the result with z01.PrintRune function, we will need to swap it back to string, so understanding of **Itoa and Atoi functions are needed for this exercice.**  

### PrintStr function
We will use a simple function called PrintStr that will allow us to print strings.
```go
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}
```
## Doop step by step

### First step

We check if the lenght of our argument is **exactly 4** (2 numbers 1 operand and the name of the file).  
If not, then we end the programm.
```go
if len(os.Args) != 4 {
    return
  }
```

### Second step

We store our numbers and operand into viariable, and **convert the numbers into int.**  
```go
number1, err1 := AtoiDoop(os.Args[1])
  number2, err2 := AtoiDoop(os.Args[3])
  operator := os.Args[2]
  result := 0
  if err1 != nil || err2 != nil {
    return
  }
```
If one of our error variable isn't nil, that means that our numbers have letters in them, so we can't performs  arithmetic operation.  
If that's the case, we just end the programm.  

### Third step

We then check for overflows, if we don't know the int overflow values, we just use the ones given in the example.  
```go
if number1 > 9223372036854775806 || number2 > 9223372036854775806 || number1 < -9223372036854775806 || number2 < -9223372036854775806 {
    return
  }
```

### Fourth step

We need now to perform the arithmetic operation on our 2 numbers.  
We use the switch case, it will detect what operand we have and perform the operation accordingly.  
```go
switch operator {
  case "+":
    result = number1 + number2
  }
```
We have to pay attention to "/" and "%" that can't be done with the second number being equal to zero.  
We then add a condition that end the programm if that happend.
```go
case "/":
    if number2 == 0 {
      PrintStr("No division by 0")
      return
    }
    result = number1 / number2
  case "%":
    if number2 == 0 {
      PrintStr("No modulo by 0")
      return
    }
    result = number1 % number2
```
In switch case, we can add something called "default", that will act like a else loop, if noone of the case is fullfilled then we execute what's inside the default.  
If the second argument is equal to noone of the operands, then we end the programm
```go
default:
    return
```
The switch case should now looks like this:
```go
switch operator {
  case "+":
    result = number1 + number2
  case "-":
    result = number1 - number2
  case "*":
    result = number1 * number2
  case "/":
    if number2 == 0 {
      PrintStr("No division by 0")
      return
    }
    result = number1 / number2
  case "%":
    if number2 == 0 {
      PrintStr("No modulo by 0")
      return
    }
    result = number1 % number2
  default:
    return
  }
```

### Fifth and final step

We now have to print the result, for that we will use the **Itoa function to tranform it to a string.**  
We can then print it with our **PrintStr function** created earlier.  
```go
PrintStr(ItoaDoop(result))
```

## Full code
```go
package main

import (
	"os"
)

func AtoiDoop(s string) (int, int) {
  // implementation of AtoiDoop function
}

func ItoaDoop(n int) string {
  // implementation of ItoaDoop function
}

func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}

func Doop() {
  // first step
  if len(os.Args) != 4 {
    return
  }
  // second step
  number1, err1 := AtoiDoop(os.Args[1])
  number2, err2 := AtoiDoop(os.Args[3])
  operator := os.Args[2]
  result := 0
  if err1 != nil || err2 != nil {
    return
  }
  // third step
  if number1 > 9223372036854775806 || number2 > 9223372036854775806 || number1 < -9223372036854775806 || number2 < -9223372036854775806 {
    return
  }
  // fourth step
  switch operator {
  case "+":
    result = number1 + number2
  case "-":
    result = number1 - number2
  case "*":
    result = number1 * number2
  case "/":
    if number2 == 0 {
      PrintStr("No division by 0")
      return
    }
    result = number1 / number2
  case "%":
    if number2 == 0 {
      PrintStr("No modulo by 0")
      return
    }
    result = number1 % number2
  default:
    return
  }
  // final step
  PrintStr(ItoaDoop(result))
}
```