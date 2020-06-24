```sc

import scala.collection.mutable.ListBuffer

object ScalaDemo extends App
{
  // for each number we want to loop through each char and show all combinattions essentially, for(num){for(char){}}
  val num = List(1,2,3)
  val char = List('a','b','c')

  // Using a mapping techniuqe we can do so like below.
  val mapIt = num.filter(n => n % 2 == 0).flatMap(n => char.map(c => s"$c $n"))
  
  // Here is our for comprehension which is a bit more readable and prefered by the scala public
  val forComprehension = for {
    n <- num if n % 2 == 0
    c <- char
  } yield (s"$c $n")

  //  Here is the older way of doing it.
  var combo = new ListBuffer[String]()
  for(n <- num){
    if(n % 2 == 0) {
      for (c <- char) {
        combo += s"$c $n"
      }
    }
  }

  println(mapIt)
  println(forComprehension)
  println(combo)
}

```
