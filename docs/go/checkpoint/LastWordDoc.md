# Last Word

Last word is a function that takes a string and return the last word of that string.  

## Last Word step by step

### First step

We set 3 variables:
- **Start as an int** that will be the index of the beggining of our last word.  
- **End as an int** for the index of the ending of our last word.  
- **condition as a boolean set to true** that will be used to detect if we had our start value or not.  
```go
start := 0
end := 0
condition := true
```

### Second step

We loop over our string backwards
```go
for i := len(s) - 1; i >= 0; i-- {
}
```
Since we're gonna use i as an index, we need to start at `len(s) - 1` to avoid getting an **out of range** error.  

### Third step

We then setup 2 conditions, one for the **start index**, the other one for the **end index**.  

First condition we check if the boolean is still true and if our current letter isn't a space.  
Once we found a letter **we give to end the value of i and we set the boolean value to false to make sure it won't change that value again.**  
```go
if s[i] != ' ' && condition {
	end = i
	condition = false
}
```
Second condition we check the end of the word by looking for a space.  
Once found **we give start the value of i and set i to 0** to end the loop.  
```go
else if s[i] == ' ' && !condition {
	start = i
	i = 0
}
```
We then have this:
```go
for i := len(s) - 1; i >= 0; i-- {
    // condition for the end index
		if s[i] != ' ' && condition {
			end = i
			condition = false
      // condition for the start index
		} else if s[i] == ' ' && !condition {
			start = i
			i = 0
		}
	}
```

### Fourth and final step

Once we have index of the start and end of that last word, we can return it using:  
```go
return s[start:end+1] + "\n"
```
**The reason you need to use end+1 is because of how Go handles string slicing.** If we use only end, we will miss a letter because the index end is **not included.**

## Full code 

```go
func lastword(s string) string {
	start := 0
	end := 0
	condition := true
	for i := len(s) - 1; i >= 0; i-- {
		if s[i] != ' ' && condition {
			end = i
			condition = false
		} else if s[i] == ' ' && !condition {
			start = i
			i = 0
		}
	}
	return s[start:end+1] + "\n"
}
```