1. else can not start on its own line the compiler with throw and error, ensure it is constructed like below.
```
val x = 55
val y = 10

if (x > y){
    println(s"$x is greater than $y")
}else if(x == y){
    println(s"$y and $x are equal")
}else{
    println(s"$y is greater than $x")
}
```
