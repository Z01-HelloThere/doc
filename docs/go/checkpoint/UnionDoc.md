# Union

Union is a program that needs to takes two `string` and displays, without doubles, the characters that appear in either one of the `string`.  

## Functions

## PrintStr

We will use a function called PrintStr that will allow us to print string with the z01.PrintRune function.  
```go
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}
```

## Doubles

We will use a function called `Doubles` that will take a string containing potentially doubles and return a version of that string without any doubles.  

### First step

We initialize a boolean variable to false and a result variable that will contain our final string.  
```go
result := ""
doubles := false
```
If we encounter a double in our new string, then it goes to true.  
We reset it every new letter we range over.

### Second step

We make 2 loops, one that iterate over the given string, the other one iterating over the result string we are building.  
```go
// loop for the first string
for i := 0; i < len(s); i++ {
    // loop for the final string we are going to return
		for j := 0; j < len(result); j++ {
			if s[i] == result[j] {
				doubles = true
			}
		}
	}
```
The idea is to test every single letter of the given string with the one we are adding to `result`.  
If at some point `s[i] == result[j]` condition is fullfilled, that means we have a double and we need to ignore this letter and go to the next one.  

### Third step

Before going to the next letter of the given string, we check the boolean value, if it's false that means it's a new letter.
```go
if !doubles {
	result += string(s[i])
}
doubles = false
```
**Before going to the next letter we set the boolean value back to false.**  
It gives us that:
```go
func Doubles(s string) string {
	result := ""
	doubles := false
	for i := 0; i < len(s); i++ {
		for j := 0; j < len(result); j++ {
			if s[i] == result[j] {
				doubles = true
			}
		}
		if !doubles {
			result += string(s[i])
		}
		doubles = false
	}
	return result
}
```


## Union 

### First step

If the number of arguments is different from 2, then we return an empty string.  
```go
result := ""
if len(os.Args) != 3 {
	PrintStr(result)
	return
}
```

### Second step

We add os.Args[2] to os.Args[1].  
```go
result = os.Args[1] + os.Args[2]
```
Adding `os.Args[2]` to `os.Args[1]` will simply add os.Args[2] at the end of os.Args[1], that's how strings addition works.  

### Third and final step

We then use the Doubles function on that new string before printing it with our PrintStr function.  
```go
PrintStr(Doubles(result))
```

## Full code

```go
package main

import (
  "os"
  "github.com/01-edu/z01"
)

// function that print a string given
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}

// function that get rid of doubles in a string given
func Doubles(s string) string {
  // first step
	result := ""
	doubles := false
  // second step
	for i := 0; i < len(s); i++ {
		for j := 0; j < len(result); j++ {
			if s[i] == result[j] {
				doubles = true
			}
		}
    // third step
		if !doubles {
			result += string(s[i])
		}
		doubles = false
	}
	return result
}

func Union() {
	result := ""
  // first step
	if len(os.Args) != 3 {
		PrintStr(result)
		return
	}
  // second step
	result = os.Args[1] + os.Args[2]
  // final step
	PrintStr(Doubles(result))
}

```