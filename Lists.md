1. Defines a single level list containing the same datatypes.
```
val evens = List(2,4,6,8,10) 
```
2. Mixed single level list
```
val mixed = List[1, "here", 'h') 

//to access a single level list use the code below, list index begins at 0
mixed(1)
```
3. list of lists
```
val listNest = List(List(1,5,6), List(7,4,5), List(9,0,1)) 
```
4. Scala supports method chaining, for example
```
listNest.flatten.sorted.sum
```
