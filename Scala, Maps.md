```sc
    val myMap = Map(("a", 1), ("b", 2))
 
 //by applying the key, to the map, it will return the value asscoiated with that key.
    myMap("a")
 
 // to add to the map we can do
   val phoneBook = Map("Jim"->555,"Sam"->727,"Bob"->222)

  val sarah = "Sarah"->111
  val phoneBook2 = phoneBook + sarah

  println(phoneBook2("Bob"))
```
