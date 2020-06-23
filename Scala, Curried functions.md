```sc
object ScalaDemo extends App
{
  val doubler = (x: Int) => x * 2

  def nTimesBetter(f: Int => Int, n: Int): (Int => Int) ={
    if(n <= 0) (x: Int) => x
    else (x: Int) => nTimesBetter(f, n-1)(f(x))
  }
  
  // this will hit the doubler function 4 times, (2*2) = 4, (4*2) = 8, (8*2) = 16, (16*2) = 32
  val resBetter = nTimesBetter(doubler, 4)(2)

  println(resBetter)
}
```
