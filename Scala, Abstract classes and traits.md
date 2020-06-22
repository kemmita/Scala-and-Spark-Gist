```sc
object ScalaDemo extends App{
  var croc = new Crocodile()
  croc.kills(new Animal {
    override val creatureType: String = "K9"

    override def eats: Unit = ???
  })
  croc.swim()
}

// here we define our abstarct class. We can defin props and funcitons that will need to be defined in our sub classes.
// you may also implement a function or prop here if you choose to do so.
abstract class Animal{
  val creatureType : String
  def eats: Unit
}

// Below we create two traits, our implementation class cannot have many abstract classes, but it can have many traits
trait Carnivore {
  def kills(animal: Animal)
}

trait Swims {
  def swim(): Unit
}

// below we define our abstract class and trait props and functions.
class Crocodile extends Animal with Carnivore with Swims {
  val creatureType: String = "Reptile"

  def eats: Unit = println("Animals")

  def kills(animal: Animal): Unit = println(s"I kill ${animal.creatureType}'s")

  def swim(): Unit = println("I like to swim under water")
}

```
