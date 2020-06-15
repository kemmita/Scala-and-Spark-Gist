```sc
//0 to 10 inclusive
for(i <- 0 to 10){
    if(i%2 == 0){
        println(i)
    }
}


val list = List(1,2,3,4,5,6)
val arr = Array(99,44,55,66)
val set = Set(33,12,99)
val map = Map(('a', 1), ('b', 2))

for(i <- 0 to (list.length - 1)){
    println(list(i))
}
```
