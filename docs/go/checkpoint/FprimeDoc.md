# Fprime

## What's Fprime

Fprime is a function that takes a positive int and displays its prime factors, followed by a newline ('\n').

- Factors must be displayed in ascending order and separated by *.  

- If the number of arguments is different from 1, if the argument is invalid, or if the integer does not have a prime factor, the program displays nothing.  

The function will divide the number by the first prime number until the modulo isn't equal to 0, then it goes to the next prime number ect until it reaches 0.  

Example:
```txt
First prime number (2):
225225 / 2 = 112612.5
(rest different than 0, we ignore that operation and go to the next prime number).

Second prime number (3):
225225 / 3 = 75075
75075 / 3 = 25025
25025 / 3 = 8341.6 
(rest different than 0, we ignore that operation and go to the next prime number).

Third prime number (5):
25025 / 5 = 5005
5005 / 5 = 1001
1001 / 5 = 200.2
(rest different than 0, we ignore that operation and go to the next prime number).
```
**ect until the result of the division is equal to 0 or the current prime number is higher than the number we want to divide.**  

## PrimeNumbers function

First we will write a function that will take an int as argument and return an array containing all the prime numbers under that int given.  

### First step

We start a loop at 3, the first prime number and we stop at the index given in argument.  
```go
primenumber := []int{}
for i := 3; i < index; i++ {
		for j := 2; j < i; j++ {
	}
}
```
for each values of i, we will test them with another loop, that will go from 2 to i - 1, **because a prime number can only be divided by 1 and itself.**  

### Second step

We then initialize a boolean value and test every numbers **between 2 and i - 1** 
```go
isprime := true
for j := 2; j < i; j++ {
	if i%j == 0 {
		isprime = false
	}
}
```    
if any of the modulo is equal to 0, then that number isn't a prime number and we don't print it, otherwise we append it to our array.  

**Before incrementing i, we need to set the boolean value back to true.**

```go
func PrimeNumbers(index int) []int {
	primenumber := []int{}
	isprime := true
	for i := 3; i < index; i++ {
		for j := 2; j < i; j++ {
			if i%j == 0 {
				isprime = false
			}
		}
		if isprime {
			primenumber = append(primenumber, i)
		}
		isprime = true
	}
	return primenumber
}
```

## Fprime step by step

### First step

We first settup a vew variables:
- finalstring: string variable that will contain the final result that we want to print at the end of the function.  
- number: int convertion of our string argument (os.Args[1]).  
- index: int value that will be the index of the primenumber array 
- max: int value for the PrimeNumbers function.  
- division: int value that will store the result of the division by the prime numbers.  
- primenumber: array that will store the primenumbers under max.  
```go
finalstring := ""
number, err := strconv.Atoi(os.Args[1])
index := 0
max := 80
division := 0
primenumber := PrimeNumbers(max)
if err != nil || number < 3 {
	return
}
```
**Checking also for input error with the Atoi convertion.**  

### Second step

We will then iterate over the primenumber array.  
```go
for index < len(primenumber) {
}
```	

### Third step

We then store the rest of the number divided by the current prime number.  
**If the rest is equal to 0 and the number is different than 1**, then we can add it to the string.  
```go
division = number % primenumber[index]
if division == 0 && number != 1 {
	// store the division made into the finalstring (without forgetting to convert it to a string).
	finalstring += strconv.Itoa(primenumber[index]) + "*"
	// dividing the number by the primenumber
	number = number / primenumber[index]
} else {
	// going to the next prime number
	index++
}
```
If not, then that means we can't divide it by the current prime number so we **increment index to go to the next prime number.**  

**Full loop:**  
```go
for index < len(primenumber) {
	division = number % primenumber[index]
	if division == 0 && number != 1 {
		finalstring += strconv.Itoa(primenumber[index]) + "*"
		number = number / primenumber[index]
	} else {
		index++
	}
}
```

### Fourth and final step

Once the loop is finished, we check the number. If it's equal to 1, then that means that the number a valid.  
**Otherwise we just return the os.Args[1].**  
```go
if number == 1 {
	PrintStr(finalstring[:len(finalstring)-1])
} else {
	PrintStr(os.Args[1])
}
```
If the number is valid we print the finalstring without the last character, which is a * in our programm.  


## Full code

```go
package main

import (
	"os"
	"strconv"
)

func PrimeNumbers(index int) []int {
	primenumber := []int{}
	isprime := true
	// first step
	for i := 3; i < index; i++ {
		for j := 2; j < i; j++ {
			// second step
			if i%j == 0 {
				isprime = false
			}
		}
		if isprime {
			primenumber = append(primenumber, i)
		}
		isprime = true
	}
	return primenumber
}

func Fprime() {
	// first step
	finalstring := ""
	number, err := strconv.Atoi(os.Args[1])
	index := 0
	max := 80
	division := 0
	primenumber := PrimeNumbers(max)
	if err != nil || number < 3 {
		return
	}
	// second step
	for index < len(primenumber) {
		// third step
		division = number % primenumber[index]
		if division == 0 && number != 1 {
			finalstring += strconv.Itoa(primenumber[index]) + "*"
			number = number / primenumber[index]
		} else {
			index++
		}
	}
	// final step
	if number == 1 {
		PrintStr(finalstring[:len(finalstring)-1])
	} else {
		PrintStr(os.Args[1])
	}
}
```