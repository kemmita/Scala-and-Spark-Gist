1. Defines a single level list containing the same datatypes.
```sc
val evens = List(2,4,6,8,10) 
```
2. Mixed single level list
```sc
val mixed = List[1, "here", 'h') 

//to access a single level list use the code below, list index begins at 0
mixed(1)
```
3. list of lists
```sc
val listNest = List(List(1,5,6), List(7,4,5), List(9,0,1)) 
```
4. Scala supports method chaining, for example
```sc
listNest.flatten.sorted.sum
```
