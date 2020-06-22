```sc
object ScalaDemo extends App{
  var i = new Info[String]
  i.Overview("Apples")
}


class Info[T] {
  def Overview(subject: T): Unit ={
    println(s"Displaying overview for $subject")
  }
}
```
