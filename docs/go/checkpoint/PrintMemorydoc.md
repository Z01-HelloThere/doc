# Printmemory

## What's Printmemory

Printmemory is a function that prints the hexadecimal representation of every values of a byte array.

## Base 10 and Base 16
We already use a base in the everyday life which is the base 10. **Base 10 means that we can have 10 different values** before going to the next digit.  
When we are at 9 and we had 1, then we go one digit to the left, which gives us 10.  

It's the exact same thing with base 16, we have **16 different values** and when we get to 16, our number is 10.  
Here is what happend:
```txt
base 10:
0 -> 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> 10  
base 16:
0 -> 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> a -> b -> c -> d -> e -> f -> 10
```
We will need to convert ascii values expressed in base 10 to base 16.

## Conversion

In the main function:
```go
printmemory([10]byte{'h', 'e', 'l', 'l', 'o', 16, 21, '*'})
```

### First step
```go
tabascii := []string{"0", "1", "2", "3", "4", "5", "6", "7", "8", "9",
    "a", "b", "c", "d", "e", "f"}
```    
We define a slice of strings that contains all hexadecimal values.

### Second step
```go
first := 0
second := 0
for i := 0; i < 10; i++ {
    first = int(rune(arr[i]) / 16)
    second = int(rune(arr[i]) % 16)
}
```
We iterate over the byte array and **store 2 values.**  
- **The result of the division by 16.**
- **The rest of the division by 16.**  
For example the letter "h" is 104 on the ascii table.   
We can divide it 6 times by 16     -> **16 x 6 = 96.**  
And the rest of this division is 8 -> **96 + 8 = 104.**  
We then have 6 and 8, **because 104 in base 16 is 68**. We just need to store it to be able to show it after.

### Third step
```go
tabascii := []string{"0", "1", "2", "3", "4", "5", "6", "7", "8", "9",
    "a", "b", "c", "d", "e", "f"}
finaltab := []string{}
first := 0
second := 0
for i := 0; i < 10; i++ {
    first = int(rune(arr[i]) / 16)
    second = int(rune(arr[i]) % 16)
    finaltab = append(finaltab, tabascii[first]+tabascii[second])
}
```
We then add an array that will append new values of the converted bytes values.  
We use the int as an index of the tabascii array for 2 reasons:
- First we have an int and it's easier to deal with string with z01.PrintRune. So that way we get the **string value of our int without converting it**  
- If our int is above 9, which is supposed to happend since we're dealing with base 16. That way if we have 10 as an int, it will convert it to "a".  

Here is what we get:
```go
finaltab = []string{"68", "65", "6c", "6c", "6f", "10", "15", "2a", "00", "00"}
```

### Fourth step
```go
for i := 0; i < 10; i++ {
    PrintStr(finaltab[i])
    if i == 3 || i == 7 || i == 9 {
        z01.PrintRune('\n')
    } else {
        z01.PrintRune(' ')
    }
}
```
We then iterate over our finaltab to print the values one by one.  
As asked we have **4 values per line**, so when i is equal to 3, 7 or 9 we need to add a "\n", otherwise it's just a space.  

Here is what we get:
```go
68 65 6c 6c
6f 10 15 2a
00 00
```

### Fifth step
```go
for i := 0; i < len(arr); i++ {
    if rune(arr[i]) >= 32 && rune(arr[i]) <= 127 {
        z01.PrintRune(rune(arr[i]))
    } else {
        z01.PrintRune('.')
    }
}
```
We print the ASCII representation of each byte, **replacing non-printable characters with a dot.**  
Printable characters on the ascii table are from 32 to 127.  

Here is what we get: 
```go
hello..*..
```

## Full code

```GO
package main

import "github.com/01-edu/z01"

func PrintStr(s string) {
    for i := 0; i < len(s); i++ {
        z01.PrintRune(rune(s[i]))
    }
}

func printmemory(arr [10]byte) {
    tabascii := []string{"0", "1", "2", "3", "4", "5", "6", "7", "8", "9",
        "a", "b", "c", "d", "e", "f"}
    finaltab := []string{}
    first := 0
    second := 0
    for i := 0; i < 10; i++ {
        first = int(rune(arr[i]) / 16)
        second = int(rune(arr[i]) % 16)
        finaltab = append(finaltab, tabascii[first]+tabascii[second])
    }
    for i := 0; i < 10; i++ {
        PrintStr(finaltab[i])
        if i == 3 || i == 7 || i == 9 {
            z01.PrintRune('\n')
        } else {
            z01.PrintRune(' ')
        }
    }
    for i := 0; i < len(arr); i++ {
        if rune(arr[i]) >= 32 && rune(arr[i]) <= 127 {
            z01.PrintRune(rune(arr[i]))
        } else {
            z01.PrintRune('.')
        }
    }
}
```
And it's result:
```go
68 65 6c 6c
6f 10 15 2a
00 00
hello..*..
```