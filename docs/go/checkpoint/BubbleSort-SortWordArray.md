# SortWordArray - BubbleSort

## What is Bubblesort and how does it work

### Purpose

The bubble-sort is an algorith that will sort an array of int or string in descending or ascending order, depending on the condition you apply inside the loops.  
For strings values it will sort then by their values on the ascii table.

### How it works  

The bubble-sort will go throught an array and **compare the curent value with the next one.**  
While comparing them, if a value is not sorted we can add a condition to swap the values.  
That way, we have to go throught the array to sort 1 value. We then repeat this process for the number of values the array store.  
**Note that the bubble-sort isn't the most efficient way to sort values.**

## Sorting

### First step

The first step consist of going throught the array.  
Note that as said above, we are going to compare **the current value with the next one, so to avoid an out of range error, we will need to stop at the lenght of the array minus 1.**

```go
tabWord := []string{"3", "2", "a", "b", "1", "c"}
for j := 0; j < len(tabWord) - 1; j++ {

}
```

### Second step

We will then compare the current value with the next one, and if it match then we will swap the values, the condition will change depending on if we want to sort in ascending or descending order.

```go
//Ascending order
if tabWord[j] > tabWord[j + 1] {
  //Easy way to swap 2 array values
  tabWord[j], tabWord[j + 1] = tabWord[j + 1], tabWord[j]
}
```
```go
//Descending order
if tabWord[j] < tabWord[j + 1] {}
```

### Third step

What we did just now only sorted a single value. Here is what happend on the entire **for** loop:  
(values in quotes are both the value and the one next to it compared)
```go
1:  "3" -> "2" ->  a  ->  b  ->  1  ->  c 
2:   2  -> "3" -> "a" ->  b  ->  1  ->  c  
3:   2  ->  3  -> "a" -> "b" ->  1  ->  c  
4:   2  ->  3  ->  a  -> "b" -> "1" ->  c 
5:   2  ->  3  ->  a  ->  1  -> "b" -> "c" 
6:   2  ->  3  ->  a  ->  1  ->  b  ->  c 
```
By doing that **we only sorted 1 value**, which is c on our example. To be able to sort that array **we will have to repeat that loop for the number of values in our array.**  
To do that we simply use a for loop:
```go
for i := 0; i < len(tabWord) - 1; i++ {
}
```

### Fourth step

The program we have up until now is enough to be able to sort array. The only problem we have is that we compare values that already are sorted.  

On each j loop, we have 1 value that is sorted, so we don't need to compare it anymore.  
So instead of stoping our j loop at **len(tabWord) - 1**, we will stop it at **len(tabWord) - 1 - i**.  
That way everytime we loop on j we do 1 comparaison less than the previous loop. **It's all about optimisation.**
```go
for j := 0; j < len(tabWord) - 1 - i; j++ {
}
```
Here is what the next steps looks like:  
**Second j loop:**
```go
1:  "2" -> "3" ->  a  ->  1  ->  b 
2:   2  -> "3" -> "a" ->  1  ->  b    
3:   2  ->  3  -> "a" -> "1" ->  b 
4:   2  ->  3  ->  1  -> "a" -> "b"
5:   2  ->  3  ->  1  ->  a  ->  b    
```
**Third j loop:**
```go
1:  "2" -> "3" ->  1  ->  a
2:   2  -> "3" -> "1" ->  a 
3:   2  ->  1  -> "3" -> "a"
4:   2  ->  1  ->  3  ->  a      
```
**Fourth j loop:**
```go
1:  "2" -> "1" ->  3 
2:   1  -> "2" -> "3"
3:   1  ->  2  ->  3    
```
**Fifth j loop:**
```go
1:  "1" -> "2"
2:   1  ->  2 
```

## Full code

```go
tabWord := []string{"3", "2", "a", "b", "1", "c"}
for i := 0; i < len(tabWord) - 1; i++ {
  for j := 0; j < len(tabWord) - 1 - i; j++ {
    if tabWord[j] > tabWord[j+1] {
      tabWord[j], tabWord[j+1] = tabWord[j+1], tabWord[j]
    }
  }
}
```
Final result:
```go
[1 2 3 a b c]
```
