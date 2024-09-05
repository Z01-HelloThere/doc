# Zipstring

## What is zipstring

zipstring is a function that takes a string and returns a new string that replaces every character with the number of duplicates and the character itself, deleting the extra duplications.

## Zipstring step by step

### First step

First since we got to print the numbers of duplicates at the beggining of the word instead of the end, we are going to **loop over our given string backwards.**  
That way we can count while we iterate throught the string and **print a number when we encounter something different.**

```go
for i := len(s) - 1; i >= 0; i-- {
}
```

### Second step

Then, we will need to add a count variable that will be **incremented everytime we encounter the same letter** as before.  

```go
count := 0
for i := len(s) - 1; i >= 0; i-- {
  if s[i] == s[i-1] {
			count++
		}
}    
```

### Third step

When the letter is different, we need to add to a result variable the letter plus the number of times it appeared and reset the count to 1 (minimum value).    

```go
result := ""
else if s[i] != s[i-1] {
	result = strconv.Itoa(count) + string(s[i]) + result
	count = 1
}
```
Keep in mind that we will need to use **Itoa function** on the count as it is a int and we want to work with strings.  
We also need to **convert s[i] to a string since that's a byte** when iterating over the string.  
Function should now looks like this:  
```go
result := ""
count := 1
for i := len(s) - 1; i >= 0; i-- {
  if s[i] == s[i-1] {
		count++
	} else if s[i] != s[i-1] {
		result = strconv.Itoa(count) + string(s[i]) + result
		count = 1
	}
}
```

### Fourth and final step

We then add a final condition that will be applied first for **the last iteration, when i is equal to 0.**  

```go
if i == 0 {
	result = strconv.Itoa(count) + string(s[i]) + result
}
```

## Full code

```go
package main

import (
	"fmt"
	"strconv"
)

func zipstring(s string) string {
	result := ""
	count := 1
  //first step
	for i := len(s) - 1; i >= 0; i-- {
    //final step
		if i == 0 {
			result = strconv.Itoa(count) + string(s[i]) + result
      //second step
		} else if s[i] == s[i-1] {
			count++
      //third step
		} else if s[i] != s[i-1] {
			result = strconv.Itoa(count) + string(s[i]) + result
			count = 1
		}
	}
	return result
}
```