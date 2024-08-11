# How to write the Itoa function

## What's Itoa

**Itoa** is the contraction of Int to Ascii.  

```txt
I[nt] to A[scii]
```

It means that we will convert an **integer** to a **string**.  
We will have to slice our number to convert each digits to it's ascii value on the ascii table.  
**For example 0 as a int will be 48 on the ascii table.**  

## Golang specificity

In golang, **you can index a string but you can't index an int**.  

That means that if we have both a string and an int that have 1234 as value:  
- for the variable: `var s string = "123"`, you can get the first value by using `s[0]` (returns "1")
- for the variable: `var s int = 123`, you can't, it will return an *NonIndexableOperand* error.

> NonIndexableOperand occurs when an index operation is applied to a value that cannot be indexed

## Conversion

### First step

```go
if n == 0 {
  return 0
}
```

If the **int is equal to `0`**, then we don't bother looping over it.  
We **return `0`**  

### Second step

```go
var isNegative bool
...
if n < 0 {
  isNegative = true
  n = n * -1
}
```

We will use a boolean variable that will store the state of the number we're about to convert.  

> note: **That step is very important because on the following steps we are going to use mathematical operators on the int so we have to make sure to get rid of the potential minus before that.**  

A boolean variable can store 2 differents values, **true** and **false**.  
If the condition is filled, then we **multiply our int by -1 to get rid of the minus** and we change our boolean value.  
That boolean value is important because it will tell our programm that we changed the value of our int.  

### Third step

```go
// We will loop while our number is superior to 0, we continue.
for n > 0 {
  // We cant index an int but one way to do it is to do the modulo by 10 to get the digit to the right of our number.
  
  // We have to have '0' to it because the range of the numbers in ascii table is from 48 to 57.
  str = string(n%10 + '0') + str

  // Divide by 10 so on the next loop we do the same for the digit to the right of the one we just did
  n = n/10
}
```

### Fourth and final step

**Finally, we check the value of our boolean, to check if we have to add `-`**

```go
if isNegative {
  return "-" + str
} else {
  return str
}
```

## Full code

```go
package main

func Itoa(n int) string{

  var isNegative bool
  var str string

  // first step
    if n == 0 {
    return 0
    }
  
  // second step
  if n < 0 {
    isNegative = true
    n = n * -1
  }
  
  // third step
  for n > 0 {
    str = string(n%10 + '0') + str
    n = n/10
  }

  // final step
  if isNegative {
    return "-" + str
  } else {
    return str
  }

}
```

<!-- todo:
- handle special case for the minimum int `if n == -2147483648` value
- handle errors return (?)
-->
