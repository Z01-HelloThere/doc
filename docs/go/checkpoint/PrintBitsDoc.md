# PrintBits

## What's PrintBits ?

PrintBits is a function that takes a number as argument, and prints it in binary value without a newline at the end.

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

## PrintBits step by step

### First step

If the number of arguments is different from 2 (number + name of the file), then we end the programm.  

```go
if len(os.Args) != 2 {
	return
}
```  

### Second step

We then settup some variables
- **result:** variable that will store the convertion of our given int.  
- **number:** int convertion of our os.Args[1].
- **base:** A string array that will contain every possible cases of our base. We can add more values if we want to change the base. (here base 2: 2 possible values).  

```go
result := ""
number, err := strconv.Atoi(os.Args[1])
if err != nil {
	PrintStr("00000000")
}
base := []string{"0", "1"}
```  
We also check for convertion error on the Atoi. If the value we want to **convert contains something else than int values, then we return 00000000.**  

### Third step

We will then **divide the number by the lenght of the base until it reaches 0.**  


```go
for number != 0 {
	result = base[number%len(base)] + result
	number = number / len(base)
}
```  

We then, inside that loop add to result the base at the index of the modulo of the number by the lenght of the base array.  
**Example: if number is 125, 125%2 equal 1, we add then base[1] to result, which is 1.**  

### Fourth and final step

Since we want to have the result shown on 8 bits, we complete if the lenght of result is inferior to 8.  
```go
for len(result) < 8 {
	result = "0" + result
}
```
And then we print the result using the **PrintStr function.**  

## Full code

```go
package main

import (
	"os"
	"strconv"
  "github.com/01-edu/z01"
)

//function that print a string given
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}

func PrintBits() {
  //first step
	if len(os.Args) != 2 {
		return
	}
  //second step
	result := ""
	number, err := strconv.Atoi(os.Args[1])
	if err != nil {
		PrintStr("00000000")
	}
	base := []string{"0", "1"}
  //third step
	for number != 0 {
		result = base[number%len(base)] + result
		number = number / len(base)
	}
  //final step
	for len(result) < 8 {
		result = "0" + result
	}
	PrintStr(result)
}
```