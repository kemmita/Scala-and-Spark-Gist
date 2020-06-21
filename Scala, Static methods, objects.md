```sc
object ScalaDemo{
 def main(args: Array[String]): Unit = {
   // Singleton static method call
   println(Person.numberOfEyes())

   // Instantiated Person class
   var person = new Person(8)
   println(person.numberOfEyes())
 }
}

object Person {
  val N_EYES = 2
  def numberOfEyes(): String ={
    s"You have $N_EYES eyes"
  }
}

class Person(val N_EYES: Int){
  def numberOfEyes(): String ={
    s"You have $N_EYES eyes"
  }
}
```
