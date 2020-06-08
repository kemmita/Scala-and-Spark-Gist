1. We can use the reduce funciton of Scala to return the sum of a list
```sc                                               
val numberList = List(1, 2, 3, 4, 5) 
val sum = numberList.reduce( (x: Int, y: Int) => x + y)

println(sum)                                      
```
