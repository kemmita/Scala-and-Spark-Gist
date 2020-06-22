1. to work with the basics of exceptions use
```sc
object ScalaDemo extends App
{
    var e = Exceptions()
    e.testIt()
}

case class Exceptions()
{
  // below we use a try catch finally statement.
  def testIt(): Unit = {
    try{
      getInt()
    } catch {
      case e : NullPointerException => println("Error!")
    } finally {
      println("Finally")
    }
  }
  def getInt(): Int ={
    throw new NullPointerException
  }
}
```

2. If we want to use custom exception handling, it is quite easy.
```sc
object ScalaDemo extends App
{
    var e = Users()
    e.ReturnUser()
}

case class Users()
{
  def ReturnUser(): Unit = {
    try{
      getUser()
    } catch {
      case e : RestExceptions => println("Error!")
    } finally {
      println("Finally")
    }
  }
  def getUser(): Int ={
    throw RestExceptions("404: Not Found!").throwRest()
  }
}

// we extend Exception and implement a new throwRest metrhod that will take in the rest error code and display it to the developer.
case class RestExceptions(exception: String) extends Exception{
  def throwRest(): Exception ={
    throw new Exception(exception)
  }
}

```
