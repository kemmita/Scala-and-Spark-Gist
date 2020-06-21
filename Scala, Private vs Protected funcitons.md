```sc
class Person(val age: Int, val name: String){
  // this class and any sub class that inherits from this class will have access to this function.
  protected def introduction(): String ={
    s"$name is $age years old"
  }
  
  //this funciton will be restirected to this class
  private def explainAge(): String ={
    if(age > 40){
      println("Your fucked!")
    }
    "Your doing great!"
  }

  def address(): String = {
    "My home address is university ave."
  }
}

// class Employee will have access to Introudction using inheritence, but will not have access to explainAge
class Employee(age: Int, name: String, salary: Double) extends Person(age, name){
  def employeeIntroduction(): String = {
    introduction() + s" with a current salary of $salary"
  }
}
```
