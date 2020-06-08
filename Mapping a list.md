1. If we want to alter the value of each elem in a list, we can use the Scala map function
```sc
val shipList = List("Enterprise", "Defiant", "Voyager", "Deep Space Nine")

val ships = shipList.map( (ship: String) => {"Ship: " +ship})

for (ship <- ships) {println(ship)}    
```
