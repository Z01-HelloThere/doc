# **Itoa doc**

## What's Itoa
Itoa is the contraction of Int to Ascii.
It means that we will convert an **integer** to a **string**<br>
We will have to slice our number to convert each digits to it's
ascii value on the ascii table.<br>
**For example 0 as a int will be 48 on the ascii table.**

## Golang specificity
In golang, you can index a string but you can't index an int.

That means that if we have both a string and an int that have
1234 as value:<br>
for a string named s: you can get the first value by using s[0]<br>
**Notice that you can't use that method for an int.**
<br>

## Conversion
### **First step**
We will use a boolean variable that will store the state of the number we're
about to convert.<br>


**That step is very important because on the following steps we are going to use mathematical<br>
operators on the int so we have to make sure to get rid of the potential minus before that.<br>**


A boolean variable can store 2 differents values, true and false.<br>
if the condition is filled, then we **multiply our int by -1 to get rid of the minus** and we change our boolean value.<br>
That boolean value is important because it will tell our programm that we changed the value of our int.<br>

### **Second step**
If the **int is equal to 0**, then we don't bother looping over it, we **return "0"**.

### **Third step**
```go
We will loop while our number is superior to 0, we continue.
for n > 0 {
  We cant index an int but one way to do it is to do the modulo by 10
  to get the digit to the right of our number.
  
  We have to have '0' to it because the range of the numbers in ascii table is from 48 to 57.
  str = string(n%10 + '0') + str

  Divide by 10 so on the next loop we do the same for the digit to the right of the one we just did
  n = n/10
}
```

### **Fourth and final step**
**Finally, we check the value of our boolean, to check if we have to add "-"**<br>
```go
if isNegative {
  return "-" + str
} else {
  return str
}
```





