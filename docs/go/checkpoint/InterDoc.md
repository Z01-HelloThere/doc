# Inter

## What's Inter

Inter is a function that takes two string and displays, without doubles, the characters that appear in both string, in the order they appear in the first one.

## DoublesInter step by step

### First step

We iterate over the second string.  
```go
for i := 0; i < len(s); i++ {
}
```

### Second step

We then test if the **letter given is equal to any of the string letter.**  
If that's the case, then we **return false**.  
```go
for i := 0; i < len(s); i++ {
	if letter == string(s[i]) {
		return false
	}
}
return true
```
Otherwise, we **return true.**  

## Inter step by step

### First step

First, we need to check the numbers of arguments we have.  
If it's something different that 3 (2 args and the name of the file), then we just end the programm without doing anything.  

```go
if len(os.Args) != 3 {
	return
}
```

### Second step

We then initialize 2 variables that will store **os.Args[1] and os.Args[2].**  
We also create a variable that will store the letters while iterating over the 2 arguments. That's the string we are going to use to test if there is no duplicate.  

```go
arg1 := os.Args[1]
arg2 := os.Args[2]
result := ""
```

### Third step

We need to iterate over our first argument.  

```go
for i := 0; i < len(arg1); i++ {
}
```
Inside that loop we want to iterate over the second argument.  
That way for each letter, we are going to iterate over the second argument to look for that specific letter.  

```go
for i := 0; i < len(arg1); i++ {
	for j := index; j < len(arg2); j++ {
	}
}
```

### Fourth and final step

We will then verify if the letter from the first argument match the letter from the second one.  
We also need to use our function to see if that new letter isn't a duplicate.  
```go
if arg1[i] == arg2[j] && DoublesInter(string(arg1[i]), result) {
	z01.PrintRune(rune(arg1[i]))
	result += string(arg1[i])
}
```
If all the conditions are met, then we print that letter and add it to the result string.  
**That result string will help us to keep track of the previous letters** for the Doubles function.  

## Full code 

```go
package main

import (
	"os"

	"github.com/01-edu/z01"
)

func DoublesInter(letter, s string) bool {
  //first step
	for i := 0; i < len(s); i++ {
    //second step
		if letter == string(s[i]) {
			return false
		}
	}
	return true
}

func Inter() {
  //first step
	if len(os.Args) != 3 {
		return
	}
  //second step
	arg1 := os.Args[1]
	arg2 := os.Args[2]
  result := ""
  //third step
	for i := 0; i < len(arg1); i++ {
		for j := 0; j < len(arg2); j++ {
      //final step
			if arg1[i] == arg2[j] && DoublesInter(string(arg1[i]), result) {
				z01.PrintRune(rune(arg1[i]))
				result += string(arg1[i])
			}
		}
	}
}
```