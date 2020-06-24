```sc
 val myMap = Map(("a", 1), ("b", 2))
 
 //by applying the key, to the map, it will return the value asscoiated with that key.
 myMap("a")
 
 //below we create a mutable map and append a new value to it.
 val mutMap = collection.mutable.Map(('a', 1),('b', 2),('c', 3))
 mutMap += ('d' -> 4)
```
