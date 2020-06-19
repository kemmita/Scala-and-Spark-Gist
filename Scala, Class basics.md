```sc
object ScalaDemo extends App {
  // instantiate the class.
  var person = new Person("Russell", 30)
  // print the public class property age
  println(person.age)
  // call the class funciton
  println(person.Overview())
}

// a constructor is define inline, if you do not supply the val or var option, then the class or object calling 
// this class will not be able to do person.name
class Person(val name: String, val age: Int)
{
  // The props passed in the constructor are public as we appended them with val, if we want them to be private ommit val or var.
  def Overview():String = {
    s"My name is $name and my age is $age"
  }
}
```
