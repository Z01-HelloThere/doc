# Wdmatch

## What's wdmatch

Wdmatch is a function that takes two string and checks whether it is possible to write the first string with characters from the second string. **This rewrite must respect the order in which these characters appear in the second string.**  

## PrintStr function

We write a PrintStr function that will print a string we will give to it.  
```go
func PrintStr(s string) {
  for i := 0; i < len(s); i++ {
    z01.PrintRune(rune(s[i]))
  }
  z01.PrintRune('\n')
}
```

## Wdmatch step by step

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
We also create a variable that will store our result.  

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

### Fourth step

We then need to check if the letter from the first argument match the letter from the second argument.  
If that's the case then we need to add that letter to a result variable.  

```go
if arg1[i] == arg2[j] {
	result += string(arg1[i])
}
```

### Fifth step



## Full code

```go
package main

import "os"

func WdMatch() {
	if len(os.Args) != 3 {
		return
	}
	arg1 := os.Args[1]
	arg2 := os.Args[2]
	index := 0
	result := ""
	for i := 0; i < len(arg1); i++ {
		for j := index; j < len(arg2); j++ {
			if arg1[i] == arg2[j] {
				result += string(arg1[i])
				index = j
				j = len(arg2)
			}
		}
	}
	if result == arg1 {
		PrintStr(result)
	}
}
```