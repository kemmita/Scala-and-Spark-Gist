```sc
object ScalaDemo extends App{
  // we instantiate an employee instance, but call the person introduction method on the enxt line from the employee instance
  // using inheritence.
  var e = new Employee(54, "John Staford", 90000.0)
  println(e.introduction)
}

class Person(val age: Int, val name: String){
  // declare the method in the super class
  def introduction(): String ={
    s"$name is $age years old"
  }
}

// inorder to inherit, we must use the extends keyword along with defining the constructor properly.
class Employee(age: Int, name: String, salary: Double) extends Person(age, name){
  def employeeIntroduction(): String = {
    introduction() + s" with a current salary of $salary"
  }
}


```
