```sc
object ScalaDemo extends App{
  var e = new Employee(54, "John Staford", 90000.0)
  println(e.address())
}

class Person(val age: Int, val name: String){
  def address(): String = {
    "My home address is university ave."
  }
}

class Employee(age: Int, name: String, salary: Double) extends Person(age, name){
  // we can override a method by using the override keyword. This is used when you do not want to change the method signature
  override def address(): String = {
    "My work address is capital hill."
  }
  
  // below we can inact polymorphic behaviour simply by changing the method signature.
  def address(unitChar: Char): String = {
    s"address has a unit or number of $unitChar"
  }
}
```
