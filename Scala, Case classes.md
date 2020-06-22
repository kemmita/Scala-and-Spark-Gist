1. case classes save us time while creating classes and come out of the box with companion objects.
```sc
object ScalaDemo extends App
{
    // as you can see the new keyword is not neccesarry here.
    val p = Person("Jim", 20)
    println(p.name)
}

// notice we do not needt to apply val or var to our consturcotr props
case class Person(name: String, age: Int)
{
    def yourName(): Unit = {
      println(s"your name is $name")
    }
}

```
