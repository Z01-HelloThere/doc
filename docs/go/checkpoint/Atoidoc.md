# Atoi

## What's Atoi

**Atoi** is the contraction of Ascii to Int.

```txt
A[scii] to I[nt]
```

It means that we will convert a string to an integer.
We will have to iterate over each character of the string to convert its ASCII value to its corresponding integer value.
For example, the character '0' has an ASCII value of 48, which corresponds to the integer value 0.

## Golang specificity

In Golang, you can't directly convert a string to an int.

That means that if we have a string variable s with the value "123", we can't simply use int(s) to convert it to an integer.
Instead, we need to use a loop to iterate over each character of the string and perform the conversion manually.

## Conversion

### First step

```go
if len(s) == 0 {
  return 0
}
```

If the string is empty, then we don't bother looping over it.
We return 0.

### Second step

```go
isNegative := false
...
if s[0] == '-' {
  isNegative = true
  s = s[1:]
}
```
We will use a boolean variable that will store the state of the number we're about to convert.

note: That step is very important because on the following steps we are going to use mathematical operators on the int so we have to make sure to get rid of the potential minus before that.

A boolean variable can store 2 different values, true and false.
If the condition is filled, then we set our boolean value to true and we remove the minus sign from the string.
That boolean value is important because it will tell our program that we changed the value of our int.  

```go
if s[0] == '-' {
  isNegative = true
  s = s[1:]
} else if s[0] == "+" {
  s = s[1:]
}
```
We also need to take care of the potential + sign before the number.  

### Third step

```go
var result int
for _, digit := range s {
  // We multiply the current value of result by 10 and add the new digit
  result = result * 10 + int(rune(digit)-'0')
  // We subtract '0' from the ASCII value of the character to get the corresponding integer value
}
```

### Fourth step

If we let the loop that way, it will work perfectly fine if the string the user is giving us only contains integers values. If not, when substracting our digit by '0' it will mess things up.

We will simply add an if loop to detect if we have something else than an integer. If that's the case, we return 0.  
Function will now looks like this:  

```go
for _, digit := range s {
  if digit < '0' || digit > '9' {
    return 0
  } else {
    result = result * 10 + int(rune(digit)-'0')
  }
}
```

### Fifth and final step
Finally, we check the value of our boolean, to check if we have to negate the result

```go
if isNegative {
  return -result
} else {
  return result
}
```

## Full code

```go
package main

func Atoi(s string) int {

  isNegative := false
  var result int

  // first step
  if len(s) == 0 {
    return 0
  }

  // second step
  if s[0] == '-' {
    isNegative = true
    s = s[1:]
  } else if s[0] == "+" {
    s = s[1:]
  }

  // third step
  for _, digit := range s {
  // fourth step  
  if digit < '0' || digit > '9' {
    return 0
  } else {
    result = result * 10 + int(rune(digit)-'0')
  }
}

  // final step
  if isNegative {
    return -result
  } else {
    return result
  }
}
```