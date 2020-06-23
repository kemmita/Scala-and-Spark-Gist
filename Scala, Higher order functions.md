1. Higher order funcitons apply a funciton within a function
```sc
object ScalaDemo extends App
{
  val doubler = (x: Int) => x * 2

  def nTimes(f: Int => Int, n: Int, x: Int):Int = {
    if(n <= 0) x
    else nTimes(f,n-1, f(x))
  }
  
  // this will apply f 3 times with an initial x val of 2, this will return a res of 16
  // = 2*2 = 4 = 4*2 = 8 = 8*2 = 16
  val resTwo = nTimes(doubler, 3, 2)

  println(resTwo)
}
```
