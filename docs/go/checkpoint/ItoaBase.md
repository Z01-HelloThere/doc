# ItoaBase

## ItoaBase is the contraction of Int to Ascii in a specific base.
```txt
I[nt] to A[scii] in a specified Base
```
It means that we will convert an integer to a string in a specific base (e.g. binary, octal, hexadecimal, etc.).
We will have to slice our number to convert each digit to its corresponding value in the specified base.  
The base will have to be between 2 and 16.

## Golang specificity
In golang, you can index a string but you can't index an int.

That means that if we have both a string and an int that have 1234 as value:

for the variable: var s string = "123", you can get the first value by using s[0] (returns "1")
for the variable: var s int = 123, you can't, it will return an NonIndexableOperand error.  
NonIndexableOperand occurs when an index operation is applied to a value that cannot be indexed.

## Conversion

### First step

```go
basetab := []string{"0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "A", "B", "C", "D", "E", "F"}
```
We first initialize an array that will contain all possible values from base 2 to base 16.

### Second step
```go
if value == 0 || base < 2 || base > 16 {
  return "0"
}
```
If the int is equal to 0, or the base is out of range **(less than 2 or greater than 16)**, then we return "0".

### Third step
```go
if value < 0 {
  isNegative = true
  value = value * (-1)
}
```
We will use a boolean variable that will store the state of the number we're about to convert.
If the number is negative, we set the boolean to true and multiply the number by -1 to get its absolute value.

### Fourth step
```go
for value != 0 {
  result = basetab[value%base] + result
  value = value / base
}
```
We will loop until the value is 0.  
In each iteration, we take the **remainder of the value divided by the base (value%base)** and use it as an index to get the **corresponding value from the basetab array.**
We then add this value to the result string and **divide the value by the base to move to the next digit.**

### Fifth and final step
```go
if isNegative {
  return "-" + result
} else {
  return result
}
```
Finally, we check the value of our boolean, to check if we have to add a - sign to the result.

## Full code
```go
package main

import "fmt"

func itoabase(value, base int) string {
  result := ""
  isNegative := false
  // first step
  basetab := []string{"0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "A", "B", "C", "D", "E", "F"}
  
  // second step
  if value == 0 || base < 2 || base > 16 {
    return "0"
  }
  
  // third step
  if value < 0 {
    isNegative = true
    value = value * (-1)
  }
  
  // fourth step
  for value != 0 {
    result = basetab[value%base] + result
    value = value / base
  }
  
  // final step
  if isNegative {
    return "-" + result
  } else {
    return result
  }
}
```
