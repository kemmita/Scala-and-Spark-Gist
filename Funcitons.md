```
val list = List(1,2,3,4,6,7)

def even(num:Int): Boolean = {return num % 2 == 0}

even(10)

def containsEvens(list:List[Int]) : Boolean = {
    for(elem <- list){
        if(elem%2 == 0){
            return true
        }
    }
    return false
}

containsEvens(list)

def luckyNumber(list:List[Int]): Int = {
    var sum = 0; 
    for(elem <- list){
        if(elem == 7){
            sum+=14
        }else{
            sum+=elem
        }
    }
    return sum
}

println("Sum")
list.sum

luckyNumber(list)

def balance(list:List[Int]): Boolean = {
    if(list.length % 2 == 0){
        return true
    }
    return false
}

balance(list)

def palindrome(word:String): Boolean = {
    if(word.equals(word.reverse)){
        return true
    }
    return false
}

palindrome("kayak")
```
