```sc
object ScalaDemo extends App {
  var person = new Person("Russell", 30)
  println(person.Overview())
  println(person.Overview(84000.00))
}


class Person(val name: String, val age: Int)
{
  def Overview():String = {
    s"My name is $name and my age is $age"
  }
  // simply override the method by changing the signature
  def Overview(salary: Double):String = {
    s"My name is $name and my age is $age and I make $salary dollars per year."
  }
}
```
