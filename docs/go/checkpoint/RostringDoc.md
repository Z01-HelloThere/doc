# Rostring

Rostring is an exercice that ask you to move the first word at the end of a sentence.


## Functionality

### PrintStr function

The PrintStr function takes a string as an input and prints it to the console using the z01.PrintRune function.  
It's a simplified fmt.Print function to print strings.
```go
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}
```
### Spaces function
The Spaces function takes a string as an input and returns a new string with consecutive spaces removed.  

```go
func Spaces(s string) string {
  result := ""
  spaces := false
  for i := 0; i < len(s); i++ {
    if s[i] != ' ' {
      result += string(s[i])
      spaces = true
    } else if s[i] == ' ' && spaces {
      result += " "
      spaces = false
    }
  }
  return result
}
```
We first set the boolean value to **false** and the only way for the programm to add a space is when the boolean is set to **true**.  
```go
spaces := false
```
The only way for that boolean value to be set to true is to detect something that is not a space.  
```go
if s[i] != ' ' {
      result += string(s[i])
      spaces = true
    }
```
And everytime we add a space, we set it back to false, that way we can't have consecutives spaces.  
```go
else if s[i] == ' ' && spaces {
      result += " "
      spaces = false
    }
```

## How it works
The Rostring function checks if the input string has **exactly one argument**. If not, it prints a newline character and returns.  
```go
if len(os.Args) != 2 {
    z01.PrintRune('\n')
    return
  }
```
It calls the Spaces function to remove consecutive spaces from the input string.  
```go
word := Spaces(os.Args[1])
```
It finds the end of the first word, and store the index in a variable.  
```go
end := 0
  for i := 0; i < len(word); i++ {
    if word[i] == ' ' {
      end = i
      i = len(word)
    }
  }
```
We then use the function PrintStr to print a string.  
- We print the sentence that will start at the end of the first word so we don't repeat the first word 2 times.  
- We then add a space between them.  
- And then we print only the first word, which is the sentence that stops at the index end that we got earlier.  
- To be sure that we don't have any consecutive spaces we use the Spaces function on that string.  
```go
PrintStr(Spaces(word[end:]) + " " + word[:end])
```

## Full code
```go
package main

import (
	"os"

	"github.com/01-edu/z01"
)

// function that take care of consecutive spaces
func Spaces(s string) string {
  result := ""
  spaces := false
  for i := 0; i < len(s); i++ {
    if s[i] != ' ' {
      result += string(s[i])
      spaces = true
    } else if s[i] == ' ' && spaces {
      result += " "
      spaces = false
    }
  }
  return result
}

// function that will allow us to print a string
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}

// main function
func Rostring() {
  if len(os.Args) != 2 {
    z01.PrintRune('\n')
    return
  }
  word := Spaces(os.Args[1])
  end := 0
  for i := 0; i < len(word); i++ {
    if word[i] == ' ' {
      end = i
      i = len(word)
    }
  }
  PrintStr(Spaces(word[end:]) + " " + word[:end])
}
```