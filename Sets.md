1. like in Math, sets will not conatin any duplicates, sets can be declared as mutable if needed.
```
val set = Set(22,55,33,22,55,33,55)

// the above set will be reduced to 
Set(22,55,33)

//If you want to decalre a set as mutable so that later on you can append a new value that is not already contained within the set,
//You can do
val a = collection.mutable.Set(5,6,7)

//To append a new value, use += 
a += 88
```
